---
title: "Help... need SIP softphone that actually WORKS"
date: 2009-04-27
forum: General Help
---

### Post by Thanh-BKK on 2009-04-27
Hi there.

As top[ic title says... i need recommendations for softphones that work with SIP accounts and actually WORK at all.

Tried Ekiga, Linphone and the Linux-Version of X-Lite - neither does anything useful, and all three require master degrees in advanced computer science to set them up. Honest.  I am using XC-Lite (Windows) at work, it's as easy as 1-2-3, but the Linux version.... gosh, like assembling a moon rocket. Plus it times out on every call attempt and freezes right thereafter.

Ekiga stated it is "registered" however calls go nowhere. Also won't allow to set the volume of microphone or speakers, the sliders always return to zero. L

LinPhone doesn't reveal how to get the SIP account settings in there..... so it's dead in the water.

Appreciate any input... i am fully convinced that a working one is somewhere out there.

Kind regards.....

Thanh

---

### Post by john_navarro on 2009-04-27
Try twinkle - it's in synaptic

It's what I use on a daily basis.

---

### Post by Thanh-BKK on 2009-04-27
Hi :)

Well that doesn't work either. "Registration succeeded" - nothing new, i know my account is ok.... and then "Call failed - unsupported media type" WTF..??

I think i'll have to stick with Windows to make VoIP calls to regular phones.

Best regards....

Thanh

---

### Post by Thanh-BKK on 2009-04-28
So, i'm back :)

Problem solved. After X-Lite and EyeBeam both failed as well (Windows XP virtual machine) i contacted the VoIP provider - and found out that they had changed servers (!) during the last two weeks. No wonder it wouldn't work.

So now i got EyeBeam (under Wine) and X-Lite (Linux version) as well as Twinkle working perfectly.

Best regards....

Thanh

---

### Post by hipitihop on 2009-07-18
Could someone share how they got x-lite working in ubuntu jaunty. I downloaded x-lite 2.0 from here [http://storage.counterpath.com/downloads/X-Lite_Install.tar.gz?platform=linux&product=xlite](http://storage.counterpath.com/downloads/X-Lite_Install.tar.gz?platform=linux&product=xlite) but when running from terminal it clearly struggles with audio although the GUI appears.
Othwerwise I have no problem with sound on my machine in general or Skype and other things.

Any help would be appreciated:

-----------------------
./xtensoftphone 
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
I/O warning : failed to load external entity "/home/denis/.Xscrc"
Warning: /dev/dsp appears to be a valid audio device, but I cannot
         open it.  Please ensure that no other applications are
         using the audio device (perhaps by trying ``lsof /dev/dsp'').
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so

---

### Post by freakalad on 2009-07-30
I can concur with these assessments: VoIP SoftPhones on GNU/Linux are an absolute nightmare!

Our company is currently doing work in VoIP, and even though there are some really fantastic VoIP servers (SIP via FS, in our case), like Asterisk & FreeSwitch, the SoftPhones leave a helluva lot to be desired.

If the SoftPhones themselves are not giving trouble, it's the underlying sound systems: Pulse

At present, the most stable solution I've been able to work out, is to use Twinkle, but this has some serious issues with Pulse & other software making use of the audio hardware. It's a case of EITHER VoIP OR everything else (i.e. media player), but not both.
Even Skype behaves itself better, which is absolutely shocking!

I'm busy assessing:
* Twinkle - most stable thus far, but still far from perfect. Hardware conflict issues with other sound & subsystems: it either needs to take control/ownership of audio devices, or if I'm able to get it to oth with other systems, should is corrupted/choppy
* Ekiga - stability & dependability/connectivity issues. VERY touch & go. I'd prefer to use this, but stability is a big concern.
* linphone - registration is a nightmare. seems iffy
* X-lite - really not to keen on this. This is currently the preferred platform for windows.
* Telepathy over Empathy - rocket science, can't get this to work (more RTFM for me l8r)
* Qutecom - broken
* SIP Communicator - Java....for what it's worth

I'm trying to get a simple solution together that I can document & explain in a very simple manner to laymen to clients.
I'm trying to convert people over to Ubuntu/Linux from windows, but if this is the sort of constant hacking that's required to do something that's incredibly simple on any windows box, I'll be hard-pressed to convert anyone

If anyone is able to help out, please do.

So, assume a basic setup:
* Netbook/Desktop with a pretty standard Ubuntu gnome
* PulseAudio is installed as default
* Users do more than one task at any given time, like browse the web, youtube, listen to music & possibly have Skype running
* Making use of some IM: either through Pidgin, Empathy, amsn... along those lines

So, if a user signs up for a SIP VoIP account, what software can they simply download & install (from add/remove GUI or `apt-get install .... `), without ANY hacking, enter their ID, PWD, & SIP realm/gateway/proxy?

please advise

---

### Post by Thanh-BKK on 2009-07-30
Hi :)

Off-Topic but i also noticed this "hijacking of audio devices" under Ubuntu - although for me it is Firefox which does that! 

Whenever i happen to hit a web site that plays audio (any site really, or YouTube) and later i want to play some mp3 or video from my computer with one of the installed players then i won't have sound - until i completely close Firefox. Which can be annoying if i just happen to have 26 tabs open....... 

Best regards.....

Thanh

---

### Post by inspired on 2009-08-15
I have also had reasonable success with Twinkle. For some reason Ubuntu / Pulseaudio / Twinkle seem to go out of wack with regards to mic input etc. from time to time and I have to fiddle and find workable settings again. But otherwise it works well.

SIP Communicator was also looking very promising when I first installed it. Now (a few updates latter) I can't get any sound setting to work... so I have had to ditch it. Otherwise it looked great, and worked great... at first.

Regards,
Jonathan

---

### Post by FirstByté on 2009-08-16
Yes some folks have gotten Ekiga to work 'behind' firewalls... How do I fix mine? It seems my port is blocked by my ISP...

I hope Twinkle would save my head. I was able to call KPhone's callback service but crashes once too often. I just need a softphone app so I wouldn't have to launch my Windoz box again.

Can someone suggest a working softphone with least huddles. Any that works I'm ready to give a try.

Many thanks

---

### Post by freakalad on 2009-08-16
I've gone around the block a few times now with numerous SIP softphones (looking for an option that we can push out to production & support), and thus far, Twinkle had been best (least complicated & best quality & config options), although there are SIGNIFICANT hurdles to cross, especially when dealing with PulseAudio.

Seems that Twinkle & PulseAudio do not work well together *at all*, and there are added complications when you throw KVM into the mix too (KVM clashes/locks up ALSA/PA)

* Ekiga seems like the application I'd like to end up with, but I'm experiencing buggy issues
* SIP Communicator seems nice, but still a ways off from near production-standard
* Empathy/Telepahy is a no-go, since configuration is pretty-much non-existent
* QuteCom/Wengo: seems ideal, but again configuration is an issue

(please keep in mind that I'm trying to write this from a end-user's perspective, and not a "if-you-hack-it,it-will-work" solution)

Still, I think much of my own frustration stems from the nightmare that is PulseAudio. The technology kind of makes sense, thought the need for it to be so complicated does not

---

### Post by FirstByté on 2009-08-17
Okay!

Now, I've got my Twinkle working, I guess I might give Ekiga a shot.



**Who knows how in the world to mute my system once the headphones are plugged in? [I use Ubuntu 9.04 Jaunty]**

I need to make my calls *private :P*

---

### Post by kiridude on 2009-08-17
> 
So, if a user signs up for a SIP VoIP account, what software can they simply download & install (from add/remove GUI or `apt-get install .... `), without ANY hacking, enter their ID, PWD, & SIP realm/gateway/proxy?

Did you give Gizmo a try?

---

### Post by freakalad on 2009-08-17
> **kiridude said:**
> Did you give Gizmo a try?

I did, actually.
It's pretty cool, but it's less than ideal, due to the fact that it effectively locks you tot he Gizmo service (you define your SIP & other accounts via your online account). Also, when making call to non-voip accounts, the billing takes place via the Gizmo service & not through my own in-house Asterisk/FreeSwitch. Gizmo would then effectively be my SIP provider/gateway (in fact, you still need to log in using your Gizmo account to make use of your local service)

Gizmo if fine & good if you plan on using Gizmo as your exclusive "service provider", but that's not what I'm planning on doing at this stage.

I know that most of the other softphones are also "bound" by a default provider (like Ekiga, or even Twinkle), but these other softphones connect directly to the specified server, and not to a single provider which in turn routes the traffic.

But, when all things are said & done: Gizmo IS a really great service & piece of software, and if I was to make use of a commercial service or product (VERY well-polished), I'd rather go with something like than than another, like Skype or X-lite

(found [this site]("http://www.sipsoftware.com"), and kphone shows promise...testing...)

---

### Post by FirstByté on 2009-08-17
> (found this site, and kphone shows promise...testing...) 

I just finished removing kPhone now. Well, I don't know what I'm doing/did wrong; it keeps freezing each time I ran it lately. I can remember it worked [I could make a test call] right after I installed it a while ago.

Right now Twinkle connects to my SIP provider... Sadly I have to go to their site to check my calling balance periodically :confused:

To see that I don't have to rush to windows just to use SoftPhone is cool!:guitar:

---

### Post by Mzee nyuki mpya on 2009-09-27
I was going to try x-lite until I found this in Wikipedia:
 
"There are currently two major releases of X-Lite with radically different interfaces. X-Lite 2.0 for Linux, which uses the old X-Pro code base, and X-Lite 3.0 for Windows and Mac OS X which uses the eyeBeam code base. X-Lite 2.0 is _audio only_. X-Lite 3.0 has audio, video, and instant messaging as well as being presence-capable."

I now have Skype working, but to get it to work I had to install Empathy and have it running in the background (I didn't start an account). 
I would guess that one of the dependencies I had to install with Empathy is also needed by Skype, which manages to "borrow" it when Empathy is started. I read that Empathy is/was being considered as the default for Karmic, which might explain why some have found that Skype works better with Karmic beta than with Jaunty..

---

### Post by freakalad on 2009-09-27
I've had very few problems with Skype since day-1; even on my 64-bit OS.
I usually install it via deb-get, ubuntu-tweak. Some distro's even come with it pre-installed, which suits me fine.

I'd prefer using Empathy, but I really don't like it much (as opposed to pidgin); configuration is tricky (including AV; ALSA vs PulseAudio is an entirely different story), doesn't offer the range of plug-ins & customization currently available to Pidgin.

Thus far Twinkle still reigns supreme, though it's not (yut?) compatible with PA - ALSA-only.

---

### Post by eightdollarbeer on 2012-09-01
i always fell back on twinkle but there is a new one that works . it supports pulseaudio and has a ppa SFLPhone
here is all the info you need 
[http://sflphone.org/download/stable-release](http://sflphone.org/download/stable-release)

---

