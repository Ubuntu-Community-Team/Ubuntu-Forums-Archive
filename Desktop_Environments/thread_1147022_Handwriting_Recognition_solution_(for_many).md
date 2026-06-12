---
title: "Handwriting Recognition solution (for many)"
date: 2009-05-03
forum: Desktop Environments
---

### Post by bcw on 2009-05-03
This remains valid, but for most people my more recent [**[COLOR="Red"]Ink2Text handwriting recognition[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1733298") project will be a better choice.



Hello,

I boot Kubuntu on my Fujitsu ST5032 slate computer, and I have worked out software to allow me to use the handwriting recognition provided by Windows Tablet XP on GNU/Linux desktops.

I have full cursive and printed handwriting recognition available in Kubuntu now:

I have released the software via two SourceForge projects:

[MS Ink Server]("http://msinkserver.sourceforge.net/")
[Stylus/Handwriting Input Panel]("http://ship-project.sourceforge.net/")

The first project provides the handwriting recognition capability, and a system library that allows any program to access the service (once the program is modified to use it).  The second is a client that allows immediate desktop use of the handwriting input, and a keyboard alternate for recognition correction or direct entry (Fn keys, etc.).

The intention is that we can develop general Tablet applications now while we're waiting for a Free Software solution to the handwriting recognition problem.

Many tablets sold now include Windows Tablet XP - this allows us to use the software we paid for in the environment we want.

Please try it out, and please spread the word - I want programmers to enable the Linux desktop for handwriting input!

I also have an idea for a more convenient way to do this, and I would like to hear from any WINE programmers that are interested (I don't have that background).

Cheers,
Bret

---

### Post by froghopper on 2009-07-07
Just wanted to tell you that your Input panel works really well. You rule! This message was 'written' on Uluatn. So it can't quite understand Ubantn but then it is Microsoft- Using Kubuntu 9.04 & Vista 64bit as Server also java version "1.6.0_13" without crashes. It 's understandingly slow but it toes handle my terrible handwriting.

---

### Post by bcw on 2009-07-08
Thanks.  That's good to hear, and I'm pleased to know it works with Vista, too.

I'm really hoping people will use it as a stepping stone to add handwriting as a first-class format.  I'm busy finding work these days, but I'll get to helping with that myself.  And when the rest of the handwriting support is in place, that last little bit of writing a Free Recognition library will attract some researcher or project, and we'll be able to retire this dependency.

Cheers,
bcw

---

### Post by Mr.Kappa on 2010-01-05
I just want to say that your work is fantastic and thank you! :):):)

---

### Post by Cherry Cotton on 2010-02-17
This sounds great. My tablet came with Windows Vista, but of course I never use it... I hear it has good handwriting support, though.

The problem is, my tablet itself is the only machine in my house that runs Windows (and then, of course, only when I choose it at boot). Could I use something clever like a VM as my “networked” Windows machine? Would anyone know about this or have any other ideas?

(Yes, let’s work towards removing that dependency :D Good work, though!)

---

### Post by bcw on 2010-02-18
> **Cherry Cotton said:**
> My tablet came with Windows Vista, but of course I never use it... I hear it has good handwriting support, though.

froghopper above mentions he is using this with Vista.


> **Cherry Cotton said:**
> The problem is, my tablet itself is the only machine in my house that runs Windows (and then, of course, only when I choose it at boot). Could I use something clever like a VM as my “networked” Windows machine? Would anyone know about this or have any other ideas?

I used VMware's tool to pull the installed Windows XP Tablet into a VM (Virtual Machine), and then got an activation code from Micro$oft.  The license terms for my copy of XP allow virtualization (by not mentioning it at all as a restriction) and also allow me to connect to a server running on XP to consume web services - so there's no problem there.

The only Vista license I've seen does have restrictions on virtualisation, and with different versions and possibly different licenses for different markets, you'll have to read about that yourself.

Since you say it came with your tablet, I presume it's an OEM copy.  If it's retail, it's easy to install it into a new VM.

Do you have downgrade rights to Tablet XP (many machines do)?  My Fujitsu slate came with restore media for both versions of Windows.  That removes any license restrictions about virtualisation.

Another approach is to run a Virtual Machine that accesses the native install of Windows, but that is a bit more advanced than just virtualising it entirely.

For those issues, you're better off working with either the VMware or Sun VirtualBox forums and web sites - I have used both successfully.  They will have lots of knowledgeable people dedicated to helping you make that work, and there are more of them than there are of me.

That's the only real hurdle to get over to use this approach, but there are plenty of nerds out there standing by to help.

My XP VM only uses the 'host-only' network device so Linux can request handwriting recognition.  I don't need to worry about viruses and such - it's a 'brain in a jar' that knows nothing of the outside world.  Why bother updating it?  That just gives M$ a chance to screw it up.


> **Cherry Cotton said:**
> (Yes, let’s work towards removing that dependency

The entire scheme is a throw-away - I'll happily see it all replaced with Free Software, or a more convenient scheme (although once in place, it works well - better with the Free IcedTea Java 6 JDK it turns out).

But in the meantime, it lets us develop all the Linux tablet software we want because it works now - later we'll just jack up the Linux stuff, kick the M$ stuff off to the side, slide in the Free Recognition Solution (when someone writes it) and continue happily on with more disk space...

I'd still GREATLY WELCOME some help from a WINE programmer if any should happen by.  But that needn't stop us.

Cheers,
bcw

---

### Post by grenier on 2010-04-18
This is very interesting, but I'd rather not bog down my laptop by having a huge xp run in a VM. Somewhere on the above mentionned websites, there's written that bcw actually made a very slimmed down to 128mb version of xp.

I've found the tools to do it (nlite), but could anyone tell me what it is exactly I must keep, and what I can safely jettison from the xp tablet version? I've been an exclusive linux user for the last ten years, so I must confess I really don't know much about MS software these days... :confused:

---

### Post by bcw on 2010-04-18
Hi,

I didn't do anything special with XP.

I only use the VM for recognition, so I only have the 'host only' network connection. So, I don't run any anti-malware.

I gave it 128 MB and it uses about 300MB footprint with swap, but it works well, and I never think about it.

I don't update it - it works fine. There are no security threats, as it never contacts the outside world.

Cheers,
bcw

---

### Post by grenier on 2010-04-19
Thanks for the answer.
Is it 128mb of Ram (I don't even know if it would be possible to install xp over 128mb)?

---

### Post by bcw on 2010-04-19
Hi,

128MB of RAM for the virtual machine, and a 20GB hard drive - which is mostly not there.  Both VMware & VirtualBox provide an option for an 'expandable' virtual hard disk, so it only uses the actual space needed for files.  Mine uses less than 3GB of real space on the disk.

Not to discourage, but rather to encourage, may I suggest you will get better information about virtualizing from the VMware or VirtualBox forums?  Then the information will be automatically posted there for the benefit of other people searching for that sort of information.

Cheers,
bcw

---

### Post by majedaly on 2011-11-12
It would be nice if we can have this integrated with playonlinux.

---

