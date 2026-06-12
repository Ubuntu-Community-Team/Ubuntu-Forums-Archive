---
title: "AMDGPU-PRO and old Kernel"
date: 2021-07-24
forum: Desktop Environments
---

### Post by keynoe on 2021-07-24
Hello my dear ubuntu experts,

because of a project I made my first steps to switch to Linux/Ubuntu. Encountered many challanges but until now I could solve almost all of them but one remains.

_This post is about getting amdgpu-pro driver for Fire Pro W5100 with opencl and DRM above 3.x to run houdini and prevent a lot crashes .._

I could run Houdini on Windows but my first impression was that programming on Linux/Ubuntu was more comfortable and also some of the external libraries that I need require Linux (headers).

However I can't install the latest drivers for Fire Pro W5100 (29.6.2021) because it's for older Kernels < 4.15.

I have 5 questions:
[LIST]
[*]1.Is there any workaround for using newest Kernel and newest drivers? 
[*]2.Are there any reliable sources for getting old Kernels? 
[*]3.Downsides of using old Kernels? 
[*]4.lspci -k | grep -EA2 'VGA|3D' -> *Kernel driver in use: radeon* <- shouldn't this atleast amdgpu? 
[*]5.Do you know why would AMD release newest driver for old Kernels of Ubuntu and not for RHEL/CenOS? 
[/LIST]

I wish you all a nice weekend
Key

---

### Post by mikewhatever on 2021-07-25
Just looked up info for [Fire Pro W5100]("https://www.techpowerup.com/gpu-specs/firepro-w5100.c2585"), and apparently, it only supports OpenCL 2.0. Here is another link from AMD itself [AMD itself]("https://www.amd.com/en/products/professional-graphics/firepro-w5100") with the same result.
...not much we can do about it.

---

