---
title: "Visual Effects (problem)"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by podollb on 2008-01-23
Hi, I have a nvidia card in my system at home and it works great.
> 01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
It has all the nice effects and I wanted to have the same thing on my other box, so I purchased a nvidia **NX8600GT** (T2D256E) but this one doesn't seem to work so well. If I ever try to turn on the visual effects things work kind of where the windows will disappear or the title bars will disappear and they seem to come back when I mouse over them and stuff, but it is un-usable in that state so I have to turn the effects off. It was a bummer because I like using my box with all the effects I was really looking forward to having that same thing on my new box and then eventually trying out the beyrl stuff. But I'm stuck... 
Any thoughts?

---

### Post by luisromangz on 2008-01-23
What drivers are you using? Maybe you need a newer version of the driver, for example if you are using the version Gutsy is able to install.

---

### Post by podollb on 2008-01-23
I have the restricted drivers installed for NVIDIA and they are enabled. nvidia-glx-new

The driver I seem to have is:
> 
ben@simmer:~$ sudo aptitude search nvidia
[sudo] password for ben:
p   nvidia-cg-toolkit                                            - NVIDIA Cg Toolkit installer                                           
c   nvidia-glx                                                   - NVIDIA binary XFree86 4.x/X.Org driver                                
p   nvidia-glx-dev                                               - NVIDIA binary XFree86 4.x/X.Org driver development files              
p   nvidia-glx-legacy                                            - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver                       
p   nvidia-glx-legacy-dev                                        - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files     
i   **nvidia-glx-new**                                               - NVIDIA binary XFree86 4.x/X.Org 'new' driver                          
p   nvidia-glx-new-dev                                           - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files     
v   nvidia-kernel-1.0.7184                                       -                                                                       
v   nvidia-kernel-1.0.7185                                       -                                                                       
v   nvidia-kernel-1.0.8774                                       -                                                                       
v   nvidia-kernel-1.0.9639                                       -                                                                       
v   nvidia-kernel-100.14.19                                      -                                                                       
i A nvidia-kernel-common                                         - NVIDIA binary kernel module common files                              
p   nvidia-kernel-source                                         - NVIDIA binary kernel module source                                    
p   nvidia-legacy-kernel-source                                  - NVIDIA binary 'legacy' kernel module source                           
p   nvidia-new-kernel-source                                     - NVIDIA binary 'new' kernel module source                              
p   nvidia-settings                                              - Tool of configuring the NVIDIA graphics driver                        
p   nvidia-xconfig                                               - The NVIDIA X Configuration Tool                                       


Here are more details:
> 
ben@simmer:~$ sudo aptitude show nvidia-glx-new
Package: **nvidia-glx-new**
State: installed
Automatically installed: yes
Version: 100.14.19+2.6.22.4-14.10
Priority: optional
Section: restricted/misc
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 15.2M
Depends: nvidia-kernel-100.14.19, linux-restricted-modules-common, xserver-xorg-core (>= 1:0.99.0-1), libglu1-mesa | libglu1, libatk1.0-0
         (>= 1.13.2), libc6 (>= 2.6-1), libgl1-mesa | libgl1, libglib2.0-0 (>= 2.14.0), libgtk2.0-0 (>= 2.12.0), libpango1.0-0 (>=
         1.18.2), libx11-6, libxext6, nvidia-glx
Suggests: nvidia-settings, nvidia-new-kernel-source (>= 100.14.19)
Conflicts: nvidia-glx-src, nvidia-glx, nvidia-glx-legacy
Replaces: nvidia-glx-src
Provides: nvidia-glx, xserver-xorg-video
Description: NVIDIA binary XFree86 4.x/X.Org 'new' driver
 These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server
 and supports the  newer GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and flat panel displays are also supported.
 
 If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy package instead of this one. If you have a GeForce4, you
 may need the nvidia-glx package. 
 
 To enable the driver, run "sudo nvidia-glx-config enable".


Should I downgrade to the **nvidia-glx** or **nvidia-glx-legacy**

---

