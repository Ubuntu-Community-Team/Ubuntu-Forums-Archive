---
title: "No sound out of nowhere"
date: 2009-05-17
forum: General Help
---

### Post by GreggyZed on 2009-05-17
Hi,

For about a month I have been using Ubuntu and am quite happy with it.  However, today, all of a sudden the sound in everything stopped working.  I have done nothing that I can connect to the problem.  I had previously had problems with PulseAudio so I switched everything to Alsamixer.  I think I must have removed so PulseAudio components when I was doing this because the PulseAudio in the Volume Control says "Null Output" and only shows a Master volume bar.

I have no idea what to do.  I have tried a bunch of random stuff but nothing's working and I'm concerned I will screw this up further.  Any thoughts, folks?

---

### Post by mike555 on 2009-05-17
My sound quit after updating this morning , but a restart got it working again , I hope that is all that's wrong with yours ....try restarting .

---

### Post by GreggyZed on 2009-05-17
Well, I now realize I had accidentally installed some codecs... but I can't figure out now how to get the audio working on my video files.  Flash videos have audio and I can play audio files, but when I have tried to play .wmv, .mp4, .mov files (there may be other formats not working, I just don't have them on my computer), the video plays fine but there is no audio.

Anybody know which codecs are needed for specific audios?  All the ones I can think of are installed and must be specifically related to the video itself.

---

### Post by GreggyZed on 2009-05-18
Bumpitty bump bump due to the new nature in my recently edited reply.

---

### Post by raymondh on 2009-05-18
> **GreggyZed said:**
> Bumpitty bump bump due to the new nature in my recently edited reply.

Hi Greggyzed .... have you installed ubuntu-restricted-extras ?

Raymond

---

### Post by GreggyZed on 2009-05-18
> **raymondhenson said:**
> Hi Greggyzed .... have you installed ubuntu-restricted-extras ?

Raymond


Yes, I have.  I tried removing it and installing it but still nothing.  See, recently when I was trying to fix another problem, a command I ran from the internet removed certain things (teaching me to be more careful).

I now have no sound in anything...

---

### Post by GreggyZed on 2009-05-18
As an update, I created a packages.selection file and installed everything remotely sound-related that had deinstall next to it and restarted my computer.  Sadly, there is still no sound.

Oh, and sound works when using the Live CD as well as in Windows XP.

---

### Post by zaivala on 2009-05-22
> **GreggyZed said:**
> Hi,

For about a month I have been using Ubuntu and am quite happy with it.  However, today, all of a sudden the sound in everything stopped working.  I have done nothing that I can connect to the problem.  I had previously had problems with PulseAudio so I switched everything to Alsamixer.  I think I must have removed so PulseAudio components when I was doing this because the PulseAudio in the Volume Control says "Null Output" and only shows a Master volume bar.

I have no idea what to do.  I have tried a bunch of random stuff but nothing's working and I'm concerned I will screw this up further.  Any thoughts, folks?

My first few installations of 8.04, everything worked fine.  I'm not even sure why I uninstalled.  I have not had sound since then, regardless of what other issues I have taken care of or what version is installed.  It stopped working in my 3rd installation (after working fine) and has not worked since.

I did discover that my processor was running hot, due to a clogged heatsink... of course, I didn't take action until it totally died, but the new processor (with clean, cool heatsink) is running great and still no sound.  I have, at least, gotten Jackalope installed, which I couldn't do with the old, hot processor.

And sound works fine in Windoze.

FYI, I have an Intel motherboard, which some have said has had problems in the sound department -- but if it has inherent problems, why did it work the first few installs and then quit working after a successful install?  (If anyone is interested, my machine is a HP Pavilion a1020n, and the new processor is a 3.40 GHz version of the same original 3.06 GHz Pentium 4 HT).

---

