---
title: "activate sound in XP/VirtualBox?"
date: 2009-05-24
forum: General Help
---

### Post by radi0j0hn on 2009-05-24
It may be Memorial Day weekend in the US, but for me it is "independence day" as I wiped Vista off my HP box and installed 9.04 on the whole 400 GB drive.  I had been using the 64 bit version dual booted, but I installed the 32 instead for greater compatibility with programs.

But since I need to use a couple of WINDOWS programs that require audio in and out, I need to figure out how to get my hosted XP to find the audio in VirtualBox.  The HP is pretty standard and Ubuntu had no trouble finding drivers.  USUALLY XP is also good (except with Dells!).

The programs do not play well with WINE, btw.

But XP running in a VirtualBox detects no sound device.  How should I proceed?   TIA John

---

### Post by chriskin on 2009-05-24
have you enabled audio from the setting of your virtual machine?
it has a tab called audio and you have to press to enable it

also , where is the independence if you have windows inside ubuntu instead of outside it? isn't it the same ? :P

---

### Post by radi0j0hn on 2009-05-24
I've got audio enabled, but no device can be found.  I'll check with HP and see if any driver is needed.

I'm happy to no longer dual-boot and suffer with Vista.  Running a stripped down XP virtually for ONE app I need to use is a lot better.  Also, a couple of sites (including one credit card payment site!) seem to only work with IE.  I can run XP quickly, take care of business and get out...all without rebooting.

Some day, there will be a slightly better sound app than Audacity and I'll be switched over 100%. I'm very comfortable with Adobe Audition 1.5 and use it professionally, so it is one tool I need to have access to.

I may just set up a second real PC with nothing but Audition on it for studio work.

John

---

### Post by afrodeity on 2009-05-24
Make sure you are running VirtualBox with all features, from the [Vbox site,]("http://www.virtualbox.org/wiki/Linux_Downloads") not the OSE version in the repos. You should then be able set the sound in the settings panel before you start XP. I use OSS because otherwise XP steals me Pulseaudio.

---

### Post by Solrac924 on 2009-08-12
try this:

double-click Volume Control
Change Device to "Playback: ALSA PCM...via DMA (PulseAudio Mixer)"

launch VirtualBox
when the "machine" is powered off, click Settings
click Audio
uncheck "Enable Audio" & check it again to enable it
select PulseAudio
click OK

---

### Post by fluffman86 on 2009-08-12
For your credit card website, you might want to try the User Agent Switcher for Firefox.  It makes firefox tell a website that it is actually IE for Windows and a lot of sites work that way.  

If that doesn't work, you can try [http://www.tatanka.com.br](http://www.tatanka.com.br) which does a pretty good job of running IE in Ubuntu.

Good luck finding a decent OSS or Linux-compatible sound editor, though.  I've been waiting for one for YEARS.  :(

Edit: I use Audacity anyway, and I've grown to love it even though it's not as nice as Sony SoundForge, but I won't claim to be a pro! :)

---

