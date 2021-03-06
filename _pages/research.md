---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% include base_path %}

---

## The Interweaving Project
The numerous pieces of a computer systems stack (the compiler, the OS, the 
architecture, etc.) are usually considered as separate entities. What if 
these entities weren't strictly separated -- what if these pieces were
"interwoven" or "blended"? I'm interested in exploring the feasibility, 
efficiency, and the performance of these systems -- especially at the 
intersection of the compiler and operating system layers. 

The following are projects in this research direction that I've contributed to:

- **Compiler-Timing**

  We developed the compiler-timing model as a high-performing, low-overhead 
  mechanism to replace timer interrupts and traditional interrupt handling 
  in a kernel, which is often used to drive a generic threads implementation. 
  We found that using compiler-timing to drive a fast fibers (cooperatively 
  scheduled threads) implementation in a kernel can effectively achieve 
  preemptive scheduling at a very fine-grain -- enabling the possibility
  to extract parallelism at a fine granularity. The system can perform up to
  16x faster than Linux threads. 

  The original framework achieves a soft timing guarantee by performing static 
  analyses on a piece of code and injecting callbacks that are set to execute 
  a specified interval or granularity. In other words, the compiler can be timing-aware
  using custom analyses. The original framework was written using LLVM and the Nautilus Aerokernel. (See [paper](https://souradipghosh.com/pubs-talks/)).
 
  I am currently developing a version of compiler-timing for user-space
  to drive a variety of systems using compiler-injected callbacks
  ([heartbeat scheduling](http://www.andrew.cmu.edu/user/mrainey//heartbeat/heartbeat.html),
  new techniques to analyze performance of address translation). 
 
  **In collaboration with:** Prescience Lab, NU Compilers Group, Illinois Institute 
  of Technology's [HExSA Lab](http://cs.iit.edu/~khale/lab/index.html), Carnegie Mellon, 
  NU Parallel Architecture Group

- **Compiler and Runtime-Based Address Translation** (CARAT)

  We are building on [CARAT](http://pdinda.org/Papers/pldi20.pdf), a novel framework to replace virtual 
  memory with a software implementation consisting of compiler transforms
  and a runtime. Our goal to explore an implementation of CARAT, 
  originally written in user-space, in a kernel (Nautilus). This is
  a non-trivial task, as we have to understand methods to track and 
  protect memory in the kernel, efficiently search and query memory 
  regions, apply user-space compiler transforms to the entire kernel, 
  and reduce the overhead of patching and protecting memory.
  
  See some of our [progress](https://souradipghosh.com/pubs-talks/).
 
  **In collaboration with:** Prescience Lab, NU Compilers Group, NU Parallel Architecture Group

- **Floating-Point Virtual Machine** (FPVM)

  We are expanding on work done to record the floating-point behavior
  of scientific applications ([FPSpy](http://pdinda.org/Papers/hpdc20.pdf)). We want to track and correct 
  floating-point arithmetic that generate exceptions by automatically 
  integrating codebases with an alternative FP arithmetic system. We are 
  investigating several techniques, including the use of compiler instrumentation
  to check correctness and exception state on floating-point
  operations and a custom runtime to correct erroring operations using
  the [MPFR](https://www.mpfr.org/) library.
 
  **In collaboration with:** Prescience Lab 


## Next Generation Compilers 
I'm interested in investigating and developing novel compiler optimization
and code generation techniques for the next generation of compilers. 

The following are projects in this research direction that I've contributed to:
 
- **Noelle**

  We have built Noelle as a middle-end compiler layer designed on top 
  of LLVM to provide new abstractions and parallelizing capabilities 
  that give developers the tools to build advanced code analyses and 
  transformations with just a few lines of code. 

  My research contributions include investigating and developing 
  compiler "enablers" to assist Noelle's parallelization capabilities 
  and designing and building an instruction scheduler engine for 
  users to utilize -- whether it be to parallelize code or for 
  applying custom analyses and transformations. Custom scheduling  
  techniques achieved speedups across a wide array of benchmarks
  in Noelle's benchmark suite.

  We're currently expanding the scheduler abstraction to enhance performance 
  in middle-end parallelization and reduce the memory footprint of 
  applications. The abstraction is designed as a hierarchy of schedulers
  -- with schedulers handling more and more complex control-flow structures
  (basic blocks, loops, sub-CFGs, etc.). 
  
  See some of our [progress](https://users.cs.northwestern.edu/~simonec/Software.html).

  **In collaboration with:** NU Compilers Group, Princeton's [Liberty
  Research Group](https://liberty.princeton.edu/) 

- **TimeSqueezer**

  We are expanding upon the [TimeSqueezer](https://users.cs.northwestern.edu/~simonec/files/Research/papers/RES_ISCA_2019.pdf)
  stack to further explore energy savings and efficiency with a novel 
  hardware-software co-design aimed at automatically reducing the 
  amount of memory used by instruction operands. 

  My research contributions include designing and building middle-end 
  code analyses and transformations for this new approach.  

  **In collaboration with:** NU Compilers Group, NU TimeSqueezing Group 
