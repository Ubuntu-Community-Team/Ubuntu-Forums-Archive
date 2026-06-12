---
title: "Ubuntu 20.04 issues"
date: 2021-08-25
forum: Desktop Environments
---

### Post by cscj01 on 2021-08-25
I am running Ubuntu 20.04 x64 with kernel 5.6.10-050610-generic SMP mod_unload.  I have Firefox 91.0.1.  I am also using Gnome-Flashback for my DTE.

I seem to be getting numerous failures with Firefox having to reload tabs or cannot reload them at all.  Additionally, I have had some instances where programs will not start with odd types of problems.  One example is Moneydance which has its own Java provided with the product.  When It fails I get error messages related to the system version of Java.  I have to reboot, and everything is fine for a while. Then these things start happening again.

In the case of Moneydance, I posted the error output from trying to start Moneydance from a terminal.  They said they made no calls to Java other than their own installation.  I have heard nothing back from the Firefox folks.

I am running an Intel I7-10700K CPU with no overclocking.  My system board is a Gigabyte Z490 Vision G with 128 GB of main memory and running Bios F6.

Any ideas would be appreciated.

---

### Post by T.J. on 2021-08-25
> **cscj01 said:**
> I am running Ubuntu 20.04 x64 with kernel 5.6.10-050610-generic SMP mod_unload.  I have Firefox 91.0.1.  I am also using Gnome-Flashback for my DTE.

I seem to be getting numerous failures with Firefox having to reload tabs or cannot reload them at all.  Additionally, I have had some instances where programs will not start with odd types of problems.  One example is Moneydance which has its own Java provided with the product.  When It fails I get error messages related to the system version of Java.  I have to reboot, and everything is fine for a while. Then these things start happening again.



Could you please start the affected programs in the terminal and post the errors?

---

### Post by not-published on 2021-08-25
I searched ubuntu focal packages.  "moneydance" isn't an Ubuntu pancake?

You are going to have issues a guru needs to resolve if you run software compiled under a different OS on your current OS.  That just is the way it is.

It does sound like your having Java problems.  However:  libjava.foo.so ?  libgnomefoo which relies on some lib which had a java setting changed by a non-ubuntu packege?  /usr/local/java ?  does moneydance require firefox support the same java-version ?

you may need to re-install, and if moneydance is "your core app" and you have little skills you should consider installing "exactally" the OS that was used to make the exact moneydance release your trying to use:  it may even require that you have the same hardware they do - depending on their prowess effort and skill levels.

---

### Post by cscj01 on 2021-08-25
> **not-published said:**
> I searched ubuntu focal packages.  "moneydance" isn't an Ubuntu pancake?

You are going to have issues a guru needs to resolve if you run software compiled under a different OS on your current OS.  That just is the way it is.

It does sound like your having Java problems.  However:  libjava.foo.so ?  libgnomefoo which relies on some lib which had a java setting changed by a non-ubuntu packege?  /usr/local/java ?  does moneydance require firefox support the same java-version ?

you may need to re-install, and if moneydance is "your core app" and you have little skills you should consider installing "exactally" the OS that was used to make the exact moneydance release your trying to use:  it may even require that you have the same hardware they do - depending on their prowess effort and skill levels.

I was able to get rid of the initial Moneydance problem by reinstalling.  However, with Firefox, I have not  fooled with it much.  I just use Chromium when Firefox acts up.

I have been using Moneydance for many yeears and never had issues.

Here are the messages I received when Moneydance would not start:```
/bin/sh "/opt/Moneydance/Moneydance"
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by com.bulenkov.darcula.DarculaLaf (file:/opt/Moneydance/lib/darcula.jar) to field javax.swing.text.html.HTMLEditorKit.DEFAULT_STYLES_KEY
WARNING: Please consider reporting this to the maintainers of com.bulenkov.darcula.DarculaLaf
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f9e685fc9e4, pid=76733, tid=76832
#
# JRE version: OpenJDK Runtime Environment AdoptOpenJDK (15.0.1+9) (build 15.0.1+9)
# Java VM: OpenJDK 64-Bit Server VM AdoptOpenJDK (15.0.1+9, mixed mode, sharing, tiered, compressed oops, g1 gc, linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x6e59e4]  G1ParScanThreadState::trim_queue_partially()+0x494
#
# Core dump will be written. Default location: Core dumps may be processed with "/usr/share/apport/apport %p %s %c %d %P %E" (or dumping to /opt/Moneydance/core.76733)
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid76733.log
[thread 76835 also had an error]
[thread 76800 also had an error]
[thread 76833 also had an error]
[thread 76837 also had an error]
[thread 76831 also had an error]
[thread 76836 also had an error]
[thread 76834 also had an error]
#
# If you would like to submit a bug report, please visit:
#   https://github.com/AdoptOpenJDK/openjdk-support/issues
#
Aborted (core dumped)
```I tried to pass --permit-illegal-access to the
invoking command /bin/sh "/opt/Moneydance/Moneydance" with no change in
results.  I also tried passing --illegal-access=permit with no
change as well.

I have requested the distribution that the developers use to compile Moneydance.  I'll post that when I get a response.

---

### Post by T.J. on 2021-08-26
That looks very much like the wrong version of Java.  I don't have much information on the software.  You might need an older version of Java.  I have seen  situations where Java 8 is still used, in spite of the fact that Java 8 is obsolete.  Have you tried an official Oracle release?

---

### Post by cscj01 on 2021-08-31
I have been away for a spell.  Here's the answer I received from Moneydance support concerning Java.> The java parts of Moneydance are compiled on a mac, but that shouldn't matter the distribution because the openjdk (which is bundled with moneydance) abstracts the platform part of it away. The OpenJDK is currently the linux AdoptOpenJDK version 15.0.2, and I don't know which distribution that is compiled on, but it is tagged as for glibc 2.12 and higher.

The RPM packaging is done using a tool (install4j) which does the packaging, but runs on the mac, so I imagine it has some sort of template into which it plugs in the specific parameters needed to launch moneydance. But either way, I wouldn't think that would be dependent upon which distribution it was originally built.Maybe that will give some of you some clues as to what is going wrong.

---

### Post by cscj01 on 2021-10-05
After an extended absence for an illness, I am back to see if someone can help me make progress on this.  All the same things are happening as before with the addition that Chromium is having some of the same issues as Firefox.  I am beginning to think there may be something in my configuration that is causing the instability.  One thing is a Bios setting for my memory setting.  There is a setting called Extreme Memory Profile (XMP).  This cannot be set unless the memory is paired in the slots (1 & 3) or (2 & 4) or all slots with the same sizes.  Initially, I did not have this set because I had not populated all the slots.  I am fairly sure this started happening after I populated all 4 slots.  The explanation is that XMP allows the Bios to read the SPD data on XMP memory modules to enhance memory performance when enabled.  I can't see why this would cause the issues I am having, but it seems to be something that could be checked.  Has anyone using this Mobo using XMP had any instability with their systems under 20.04?  I have seen some issues with other Mobos where XMP caused problems.  Just wondering.

---

### Post by cscj01 on 2021-10-06
Okay, I have tracked down the Firefox issue.  I found the solution here: [https://forum.andronix.app/t/ubuntu-20-04-firefox-shows-gah-your-tab-just-crashed/940/8]("https://forum.andronix.app/t/ubuntu-20-04-firefox-shows-gah-your-tab-just-crashed/940/8")
After setting the sandbox values as shown by TwilyHoney the tab crashes are gone.  Now, to fix the other issues.

---

### Post by ActionParsnip on 2021-10-06
Remember to mark as solved

---

