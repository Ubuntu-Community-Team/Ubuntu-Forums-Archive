---
title: "No Sound on Fresh 8.10 Install"
date: 2009-04-01
forum: General Help
---

### Post by dsDoan on 2009-04-01
I recently installed Ubuntu 8.10 alongside a Windows 7 partition.  Under Windows 7 sound works fine, but I can't get any sound at all under Ubuntu.  I've searched for and followed several guides trying to fix the problem, but still nothing.  Any ideas?

Mobo is [[COLOR="Blue"]_Asus P5Q SE PLUS_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131347")
Onboard Audio: VIA VT1708s

---

### Post by deffjammer on 2009-04-10
I am in the same boat with that onbard audio chip. 
Mobo; ASRock A790GHX, 
installing 8.10, 64 bit.

I followed this thread to upgrade the alsa modules, etc.  
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
  

It got me a little closer, (I think)  At least now I see the VT1708S with;
>aplay -l 
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

But I'm troubled by how it shows in;
> lscpi -vv | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)

I have a PVR card installed as well, but haven't even started looking into getting that to work. 

I'm trying to get sound working through HDMI, and from what I've read in other forums  the aplay -l command should show [HDA ATI HDMI], instead of what I have.

I'll keep looking around and trying diff module params, hopefully someone will have a new idea or solution for us.

---

