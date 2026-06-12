---
title: "video not displaying"
date: 2022-08-08
forum: Desktop Environments
---

### Post by dgermann on 2022-08-08
Friends--

Not sure what is going on, nor even what is the problem.

Immediate symptoms: installed calibre ebook reader. It can load books to my kindle paperwhite and I can read them there. But when I try to open them in calibre's reader, nothing happens.

Other symptoms I've noticed: display has seemed a little strange over the past few weeks since I installed my nvidia driver. Screen on Firefox will lock up and I have to minimize then maximize the screen to get pages to display properly. In LibreOffice if I highlight a couple of paragraphs, the highlight might not go away when I click out of the highlight area. Sometimes libreoffice actually locks the screen for some time, and I cannot alt-tab.

What I've done: I posted to the calibre user forum and Kovid Goyal the developer of Calibre responded: 
> You are missing GPU drivers. The viewer needs to be able to use OpenGL. Either install/update/unbreak your GPU drivers or try turning off hardware rendering as described here: [https://doc.qt.io/qt-6/qtwebengine-debugging.html](https://doc.qt.io/qt-6/qtwebengine-debugging.html)


However, he has no experience with nvidia devices, so was unable to help further.

History: On July 21, 2022, I ran 
```
doug@wind:~$ sudo ubuntu-drivers autoinstall
```
and installed nvidia-driver-515, which was the recommended driver. It fixed some issues I was having then, which I thought were Internet related, but seems to have been the wrong driver (nouveau) using up lots of resources.

Some details and clues:

Running a debug on opening some books in Calibre:
```
Using calibre Qt style: True
calibre Debug log
calibre 6.2.1  embedded-python: True
Linux-5.4.0-122-generic-x86_64-with-glibc2.31 Linux ('64bit', 'ELF')
('Linux', '5.4.0-122-generic', '#138-Ubuntu SMP Wed Jun 22 15:00:31 UTC 2022')
Python 3.10.1
Interface language: None
Successfully initialized third party plugins: DeDRM (7, 2, 1)
calibre 6.2.1  embedded-python: True
Linux-5.4.0-122-generic-x86_64-with-glibc2.31 Linux ('64bit', 'ELF')
('Linux', '5.4.0-122-generic', '#138-Ubuntu SMP Wed Jun 22 15:00:31 UTC 2022')
Python 3.10.1
Interface language: None
Successfully initialized third party plugins: DeDRM (7, 2, 1)
QPA platform: xcb
devicePixelRatio: 1.2916666666666667
logicalDpi: 96.0 x 96.0
physicalDpi: 74.00862745098038 x 73.98745644599303
[0.00] Starting up...
[0.00] Showing splash screen...
[0.11] splash screen shown
[0.11] Initializing db...
[0.16] db initialized
[0.16] Constructing main UI...
[0.75] main UI initialized...
[0.75] Hiding splash screen
Starting QuickView
WebEngineContext used before QtWebEngineCore::initialize() or OpenGL context creation failed.
QGLXContext: Failed to create dummy context
Failed to initialize graphics backend for OpenGL.

(evince:364266): Gtk-WARNING **: 17:04:25.961: Could not load a pixbuf from icon theme.
This may indicate that pixbuf loaders or the mime database could not be found.
WebEngineContext used before QtWebEngineCore::initialize() or OpenGL context creation failed.
QGLXContext: Failed to create dummy context
Failed to initialize graphics backend for OpenGL.
WebEngineContext used before QtWebEngineCore::initialize() or OpenGL context creation failed.
QGLXContext: Failed to create dummy context
Failed to initialize graphics backend for OpenGL.
[52.59] splash screen hidden
[52.59] Started up in 52.59 seconds with 624 books
Worker Launch took: 0.00 seconds
Worker Launch took: 0.00 seconds
Worker Launch took: 0.00 seconds
```

Other tests I ran today:

Here's what nvidia settings show:

```
Sync to VBlank (checked)
Allow Flipping (checked)
Image Settings (set to Quality--other choice are High Quality, Performance, High Performance)
Use Conformant Texture Clamping (checked)
Enable Graphics API Visual Indicator (not checked)

```

Also these:
```

doug@wind:~$ sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: GP106 [GeForce GTX 1060 3GB]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:39 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
  *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:35 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
doug@wind:~$ sudo glxinfo | grep OpenGL
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  152 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)
  Value in failed request:  0x0
  Serial number of failed request:  110
  Current serial number in output stream:  111
doug@wind:~$ sudo nvidia-smi
Failed to initialize NVML: Driver/library version mismatch
doug@wind:~$ prime-select query
on-demand
```

I also checked in synaptic and found no openGL drivers. I did find a driver here:
[https://www.nvidia.com/en-us/drivers/unix/]("https://www.nvidia.com/en-us/drivers/unix/"). I am nervous to install it for fear it might break my nvidia install.

My system: Ubuntu 20.04.4; three screens.

That's it, other than to say I am lost, and I suspect it's easy for those who know what you're seeing in these clues.

So, what should I be trying and doing next?

Thanks!

---

### Post by TheFu on 2022-08-08
I have the 5.4.x Linux kernel and nVidia GT 1030.  The correct driver for my system is the 470.x.x version.  Drivers are tied to both the hardware AND the kernel version.

Is there any chance that your system isn't using the nvidia GPU and is configured to use the Intel iGPU instead?  I think there's a tool to swap between those. I've never used it, since none of my systems have both.

---

### Post by dgermann on 2022-08-08
@ TheFu--

Thanks for responding to me.

Based upon what you wrote, I performed these commands:```

doug@wind:~$ uname -r
5.4.0-122-generic
doug@wind:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 3GB] (rev a1)
```

Then I went to [https://www.nvidia.com/en-us/geforce/drivers/]("https://www.nvidia.com/en-us/geforce/drivers/") and found a list of drivers, the top most and newest being 515.65. 

Then I went to [https://linux-hardware.org/?view=howto]("https://linux-hardware.org/?view=howto"), and it directed me to:
```
doug@wind:~$ sudo apt-get install hw-probe --no-install-recommends
doug@wind:~$ sudo -E hw-probe -all -upload
WARNING: 'edid-decode' package is not installed
Probe for hardware ... Ok
Reading logs ... Ok
Uploaded to DB, Thank you!

Probe URL: https://linux-hardware.org/?probe=ce65c3436f
```

but I am not finding a driver there.

This [https://www.intel.com/content/www/us/en/support/articles/000005520/graphics.html]("https://www.intel.com/content/www/us/en/support/articles/000005520/graphics.html") near the bottom suggests there is no one driver under linux for intel cards, and that they are usually built into the kernel. So maybe I do not need to wait to find the Xeon driver.

Would it make sense to install that nvidia driver and see if it fixes things? Ought I wait till I find the Xeon driver?

Thanks, TheFu!

---

### Post by TheFu on 2022-08-08
Never (well, almost never) get drivers anywhere except through the package manager.  There are a few exceptions for NICs, but only if the repo version isn't working at all. Typically, realtek drivers get discombobulated and break things.  Intel iGPU drivers are part of the kernel.

Switching between iGPU and add-on GPU use in Linux has a software tool for that.  I don't know what it is, since I've never used it, but I remember seeing references to it.  It isn't the "driver" or part of the drivers. It is something separate.  That's what I failed to convey in my last post.

Also, nvidia has known issues with Wayland, so X11 should always be used instead, for now.  That choice should be in the pre-login "settings" - click on the the "gear" on the login page to choose xorg or something like that.

Also, for the release you have, read the release notes, as a blank page is usually something commonly seen with workaround steps listed for boot options.  I've never needed them, but they seem to happen often enough to be documented.  I suspect it is for systems that aren't fully compliant with certain industry standards, but that's just a guess.  Over the decades, there are certain hardware vendors that I've learned to avoid either through personal experience or when hosting installfests at the local University.  Volunteering at those events is a good way to see lots of different hardware, since students show up with everything expecting to get Linux installed.

I think there's also an "ubuntu blank screen" guide that google easily finds.  Well - I can't find it now, so that isn't the correct search anymore. Sorry.  Anyway, there are a few things to try, but I really think getting the desired GPU active is the first thing to check.

---

### Post by dgermann on 2022-08-11
@TheFu --

Sorry to take so long getting back to you.

There is at least a partial resolution, and I want to ask your advice about a major thing I am thinking of trying:

1. The partial resolution: I had apparently not rebooted since I install Calibre, and maybe not since I installed the video driver. (I checked, and the additional drivers screen shows the same version of nvidia as is shown on the nvidia site. Following your advice, which seems quite sage to me, I do not want to download from the nvidia site, and will stay with what the repositories have.)

So I just now rebooted, and Calibre is working to open books, as I expected and wanted.

2. But I still have display issues. For instance, I installed PDF Studio Pro, and its screen comes up all broken up. It looks like a 10th generation photocopy of a photocopy.

What I want your advice on is whether it makes sense to upgrade to 22.04.1 when it is available in a day or two, in the hopes that that will clean up the video issues and broken dependencies and whatever else might be causing my video issues?

Thanks, TheFu!

---

### Post by TheFu on 2022-08-12
I'm not running 22.04.x (except in play VMs) and probably won't for at least a year. New is the enemy of stable and since my hardware is all well supported - well - the hardware that has any support at all - I don't need or want "new".

In the 1990s, we all chased "new" because massive improvements were happening.  That just isn't the situation anymore. 50% of "new" is stuff I don't want.

I have a deep history with PDF due to working in document management programming and deployment teams at a few companies.  I avoid using PDF unless nothing else is possible.  Nobody needs page layout control, except people working in print advertising, IMHO.  The location of each pixel and color matters then.  For for people who just want to share information, pretty much any other format is better, except a pure image.  I've seen far too many image-based PDF documents. This is a strength and a huge weakness.  

Nothing can fix a poorly scanned image inserted into a PDF.  OTOH, nothing can fix a poorly scanned image, so that isn't exactly PDF's fault.

I've used Acrobat PDF tools, a few F/LOSS tools, and some custom built tools over the decades.  They each taught me to avoid PDF. ;)

By default, I want the simplest HTML document I can get for sharing information.  epub is basically HTML, compressed. HTML is easily parsed and converts should any other format be needed.  Sometimes, even simpler formats like ASCII and markdown are even better than HTML.  I use textile markdown to create all my presentations, then convert it into S5 for fancy transitions and so anyone with a javascript-browser (or not) can access the information, for example.  I also convert the textile into formatted ASCII (this is easy), which is even better for programming people, but that loses any images and the explanation those can provide. Sigh.

---

### Post by dgermann on 2022-08-12
@TheFu--

Thank you very much!

You give sage advice.

The issue with PDF Studio Pro is with how the application itself displays, not the PDFs it pulls up--those display ok. I have asked the people at PDF Studio (they have always been responsive to me), and they have come back to me with a couple of workarounds, so apparently it is a bit of a known issue for them.

Your offhand statement, about your "hardware that has any support at all", leads me to a question I previously had no one to ask. It is off topic of this thread, so if you would like me to start a new thread, I will. The question is this: If I do not upgrade past where my computers are now (some are 18.04.x), what are the risks and downsides?

The background is this: I have closed my business and plan to shut down the computers related to it. I merely want to preserve the records for about 10 years, and then I will erase everything. I expect that every so often I will need to access some files, maybe even add some notes. It would be on a separate network without access to the Internet.

What do you think? Would you even update the OS every few years?

Thanks, TheFu!

---

### Post by dgermann on 2022-08-17
@TheFu--

Just a report back. The problems have gone away in favor of a whole new set!

I decided to upgrade to 22.04.1. It got snagged on the /boot directory being too small. I thought I could reallocate some space from another partition in LVM, but I broke the setup. As a result, I installed 22.04.1 from scratch.

Thanks for your help.

---

