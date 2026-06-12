---
title: "Programs Close Randomly"
date: 2010-02-17
forum: Desktop Environments
---

### Post by chrisolof on 2010-02-17
I've never seen this before, but for the past few days whatever I'm working on has had a tendency to close out with no warning.  Just in the last two days evince, empathy, and eclipse have closed randomly.  Since I use eclipse constantly and as a result it's been crashing the most I went ahead and started it from the command line.  Here's the output I get when eclipse closes:

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  Internal Error (psMarkSweepDecorator.cpp:50), pid=15635, tid=140400852519184
#  Error: guarantee(_destination_decorator != heap->perm_gen()->object_mark_sweep(),"Cannot advance perm gen decorator")
#
# JRE version: 6.0_15-b03
# Java VM: Java HotSpot(TM) 64-Bit Server VM (14.1-b02 mixed mode linux-amd64 )
# An error report file with more information is saved as:
# /home/chris/eclipse/hs_err_pid15635.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

```

It appears to have something to do with the "decorator," but disabling compiz all together doesn't fix it.  If anyone has any ideas I'm up for suggestions.

I'm running Ubuntu 9.10 64-bit.  The issue seems to have started shortly after installing a triple-core processor - but I'm not sure that's related.

---

### Post by chrisolof on 2010-02-18
FileZilla FTP client just closed without warning in the middle of a big transfer - fun stuff.  Just about ready to re-install Ubuntu - which is annoying - but this random closing isn't compatible with getting work done.

---

### Post by litemirrors on 2010-02-18
Whatever you do avoid Windows 7. Let me tell you what happened and why I'm on Ubuntu right now :-)

Windows 7 has a problem copying files where it will cut off in the middle of the process and leave corrupt files behind. They thought they solved it with a driver update but no dice, it destroyed everything on my external USB drive and so I said screw Microsoft. Have a look [http://social.technet.microsoft.com/Forums/en/w7itprohardware/thread/c9a12e09-78be-42c7-9a43-fd23cef6237c](http://social.technet.microsoft.com/Forums/en/w7itprohardware/thread/c9a12e09-78be-42c7-9a43-fd23cef6237c)

That's just one article, it seems this issue is not well known but for those of us that experienced it the consequences are devastating.

As for your issue it's beyond my ability since I'm knew to Ubuntu. Though I'd like to know if you fix it after reinstalling.

....... actually is Eclipse Java based? It appears to me this is a Java Runtime Error and possibly that's why they crash. It looks like Java thinks something is wrong and is the reason they close. hum 64 bit Java :\ uninstall then reinstall Java is my best guess

---

### Post by RJARRRPCGP on 2010-02-18
> **chrisolof said:**
> 

I'm running Ubuntu 9.10 64-bit.  The issue seems to have started shortly after installing a triple-core processor - but I'm not sure that's related.

Looks like you became unstable, because of a processor malfunction. 

The problem may be caused by a TLB bug. A TLB errata has been reported to occur with Phenom and possibly Athlon X3 processors.

You may be having a processor malfunction. Make sure that the BIOS selected at least the Vcore specified by AMD. 

That error may mean you motherboard isn't electrically compatible with your motherboard and thus causes the processor to compute data incorrectly.

You should test with```
mprime
``` for at least 8 hours! If it fails overnight, you have a problem.

---

### Post by chrisolof on 2010-02-19
Thanks for the tips RJARRRPCGP!

I've disabled AMD Cool'n'Quiet, which states that it may decrease the VCORE when enabled, and checked the VCORE in the bios - which is set to AUTO and sending about 1.25 V to the processor when monitored through the Hardware Monitor tab.  The spec on the processor says it's happy between 1.05 V and 1.25 V.

The processor is an AMD Phenom 8750 Tri-Core.  Brand new, stock speeds.

I didn't find mprime in the repos so I'm using StressCPU2 Stress-Test from the phoronix-test-suite package.  It's got all three cores maxed out and I've just started a six-hour run.  Tonight I'll put it into a 12-hour run if this doesn't fail.

If I do get a failure then it's not due to the Cool'n'Quiet feature that was initially on.  I think it would make sense to update the bios in that case and test again.

---

### Post by chrisolof on 2010-02-19
Alright - about three hours into the stress-test the whole system locked up completely.  I think this indicates a processor issue since it was a processor test.

I don't think this is the TLB bug though because my Phenom processor ends in "50," which indicates that it's a Revision B3 model, which isn't affected by the TLB bug.

I'm going to try updating the bios tonight in hopes that doing so resolves the issue.

---

### Post by Pro_D on 2010-02-19
I would also check your CPU frequency scaling monitor to see if ubuntu might be overclocking the system now and then.  9.10 seems to be safe from this (MUCH better communications with bios!) but in 8.04 I lost a CPU and chipset due to the ubuntu overclocking.  Symptoms were pretty similar with programs just quiting (eclipse included) often with random errors on the terminal.  I didn't notice it sooner since I was using most apps via ssh and xwindow forwarding.

---

### Post by chrisolof on 2010-02-22
I updated the bios last night to the newest available, reset everything to defaults, set the DDR2 to run at 800, and ran a cpu stress test from the [UBCD]("http://www.ultimatebootcd.com/") for 22 hours straight.  Zero errors.

Pro_D - I just verified with the CPU Frequency Scaling Monitor and a quick CPU stress test that the CPU frequency tops out at 2.4GHz, which is right where it should be.

For now I'll assume the issues were due to an outdated bios not handling the new CPU correctly.  I'll have to see how things go tomorrow before marking this as solved.

---

### Post by chrisolof on 2010-02-22
Not solved.  Eclipse is still closing with the error from the first post - only more rapidly now.  In fact it can't even finish building the workspace anymore.

Other programs, however, have been fine.

Assuming these final issues might be java or eclipse related I've reinstalled the jre and java-related packages, downloaded a fresh copy of pdt eclipse, deleted the old .metadata folder with the old eclipse workspace data, and it's still crashing.

So my next step, because I have work to get done and I can't keep eclipse up for more than a few minutes, is to work from a Live CD.  If eclipse is fine in that environment then I'll be reinstalling the whole OS - unless anyone has any further ideas.

---

### Post by chrisolof on 2010-02-24
Live CD seemed to run fine - so I reinstalled Ubuntu 9.10.  Incredibly sadly, this did not solve the issue.  Eclipse is still exiting, and now I've had Synaptic Package Manager close out in the middle of selecting packages to install (twice this happened in the last hour).  Looks like I'll be on the laptop until I can get this resolved.

Here's the kicker:  Windows XP, installed on the same machine (different partition) runs perfectly.  Games are smooth, programs stay open, and things are just perfect.

I really like Ubuntu, but if it won't allow me to get work done then I'll have to try something else.

Does anyone have any further ideas I could try to get this solved?

---

### Post by chrisolof on 2010-02-24
Also getting this "short read in buffer_copy" all of the time when trying to install software:

```
E: /var/cache/apt/archives/eclipse-jdt_3.5.1+repack~1-0ubuntu3_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/eclipse/plugins/org.eclipse.jdt.core_3.5.1.v_972_R35x.jar')
E: /var/cache/apt/archives/gcj-4.4-jre-lib_4.4.1-5ubuntu2_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/java/libgcj-4.4.jar')
```

---

### Post by chrisolof on 2010-02-25
After tonight I'm pretty certain the cause is hardware.  I was unable to reboot the system tonight - it just hung at the initial ASROCK bios screen.  Turned it off for a few hours and now it boots right up.

So tonight it runs Memtest86+ in case this might be a memory failure.

---

### Post by chrisolof on 2010-03-03
It's the CPU - no questions.  Memory checked out, as I thought it would.  This problem only presents in 64-bit operating systems, which is why Windows XP (32-bit) had no issues.  I was able to run prime95 for two days straight in 32-bit XP without any errors.  

When I ran this chip in 64-bit Windows 7 on a completely different computer (AM2+ again), the strange behavior was back.  Running the Windows Experience Index (or whatever they call it), which essentially benchmarks each piece of hardware, consistently caused a BSOD stating "A clock interrupt was not received on a secondary processor within the allocated time interval."

So yes, in the end it was the CPU and not Ubuntu's fault at all.  AMD says it might be due to a "bad register" on the chip - and they're sending out a replacement.

In the mean time I've learned that the phenom tri-core and dual-core chips are just quad-core's with one or two disabled cores because of defects.  This is called "chip harvesting."  Sometimes AMD disables the cores to meet a manufacturing quota and people have had some success unlocking the operational, disabled cores.  In my case the chip appears to have had more defects than just one bad core.

Anyway - probably a fluke, but this is the last processor I'll buy that came from "chip harvesting."  An AM3 Phenom 2 x4 Deneb 900-series is on its way from Newegg...

---

### Post by rob22941 on 2010-10-29
I'm having a similar issue gtkpod quits unexpectedly. I have an AMD Phenom 9600 quad core cpu. I'm trying to copy files from my ipod to my computer. Sometimes it runs for 5 minutes others it quits right when I start the transfer. I'm trying to copy the entire library.

---

