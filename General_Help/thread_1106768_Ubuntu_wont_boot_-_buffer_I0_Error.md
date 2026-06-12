---
title: "Ubuntu wont boot - buffer I/0 Error"
date: 2009-03-26
forum: General Help
---

### Post by Admiral Yi on 2009-03-26
Hello,
I'm having a little trouble with Ubuntu. When I start it up It does the loading bar for a bit. It never gets to the part where it actually loading, just the little orange block bouncing backwards and forwards. After a while of doing this, it goes to a text-based loading screen, where I get a few errors along the lines of: 

```
Loading hardwavre drivers
end_request : buffer 1/0 sr0
buffer 1/0 error on dev sr0
```

Im pretty sure thats what it says, but it may be slightly different. It does say some stuff about blocks at the end, but im assuming which block is going wrong isn't that important. IF it is, just ask and ill get that info for you. After this it goes on with the rest of the loading. There don't appear to be any more errors.

I have two hard drives on my computer, an 80gb one with windows xp and and a 1tb one for Ubuntu. On the Ubuntu drive I have a 100gb partition (formatted as NTFS) which I use as extra storage for windows and also so I can access files on Ubuntu easily from windows by just saving them into this extra partition. Could this be the problem? I have included a gparted screenshot that shows the layout of this hard drive. 

If anyone knows whats wrong, please help me. Ubuntu does start, but it takes a lot longer than usual. Im assuming this has something to do with my hard drives, but of course I may be wrong.

---

### Post by Admiral Yi on 2009-03-26
Bump

---

### Post by decoherence on 2009-03-26
Are you booting from the hard drive or the liveCD? Has Ubuntu ever booted for you on this hardware?

sr0 is usually an optical device (CD-ROM, DVD-ROM.) If you have a disc in there, try taking it out and booting (assuming you're not using the liveCD). If you still have a problem, open up the computer and make sure the cable that connects to the optical drive is firmly attached at both ends -- ditto for the power cable.

If you still have no luck... try just unplugging the CD/DVD and see if it boots then...

---

