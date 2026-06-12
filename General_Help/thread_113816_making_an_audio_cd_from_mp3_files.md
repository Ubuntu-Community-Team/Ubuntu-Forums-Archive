---
title: "making an audio cd from mp3 files"
date: 2006-01-07
forum: General Help
---

### Post by taseal on 2006-01-07
What program do I use?

I was gunna use k3b, but it doesnt convert the mp3 to wav files...

anything there I can use?

---

### Post by eMuNiX on 2006-01-07
Right click the track in Amarok and it gives the option to burn in either audio or data mode.

---

### Post by taseal on 2006-01-07
it says 'unable to handle the following files due to an unsupported format: mp3'

---

### Post by eMuNiX on 2006-01-07
Got Gnomebaker installed?  Click on the audio cd tab, Drag and drop the mp3's into that and click on burn audion CD it will then convert to CD audio format.

---

### Post by taseal on 2006-01-07
ugh...

```

cdrom device (/dev/hdc) is not of type generic SCSI. Setting interface to cooked_ioctl.
126976 bytes buffer memory requested, 4 buffers, 8 sectors
cooked: Read TOC : Input/output error

```

---

### Post by raggamuffin on 2006-01-07
[QUOTE=taseal]it says 'unable to handle the following files due to an unsupported format: mp3'[/QUOTE]

for .mp3 support in K3B, you need to install the **k3b-mp3** package via APT or Synaptic...

---

### Post by kronk on 2007-01-24
Package for Edgy 6.10 is **libk3b2-mp3**

Hope that helps

:guitar:

---

### Post by mptpro on 2008-07-09
I have a similar problem.

Using ubunut 8.04
amarok 1.4.9.1
k3b 1.0.4

I am having a problem when trying to create a audio-cd from mp3 files.

Amarok sends the mp3 list to k3b with no problems, but then I get the following message from k3b...

Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.

I have the "restricted-extra" installed.

I can burn mp3 using brasero.

any ideas?

---

### Post by Darkchef on 2008-07-11
just use brasero, it works fine with mp3s

---

### Post by mptpro on 2008-07-11
Thanks Darkchief,

Brassio works well.

Is there a way to get amarok to send "burn this" to brassio?

---

