---
title: "Want to stream my Windows 7 64bit to my ubuntu laptop?(32bit)"
date: 2013-03-21
forum: Gaming &amp; Leisure
---

### Post by Skrimshaw on 2013-03-21
my desktop is built to play games unlike my laptop! and i love the ability to have it in my lap anywhere but it lacks major power so how can i stream my gaming rig to my ubuntu laptop ? thanks ! ima ubuntu beginner but i know alot about windows so you can talk techy with the windows aspect but please keep ubuntu geek talk on low

EDIT- if yall need the exact specs of my desktop i built it so i can give you anything you need and the ubuntu i am running is 12.10

---

### Post by TheFu on 2013-03-21
What, specifically, exactly, do you mean by "stream"?
If both systems were running Windows, what tools/programs would you use to "stream?"

Streaming audio and video data files is relatively easy, but using a remote desktop to play games is not the same as being on the machine. Network bandwidth just doesn't have the same throughput that a directly connected GPU does.  Low end games might work, I don't know.  If you are using wifi - forget it - but it doesn't hurt to try.

The tools that you'd want to look into are:
* Remote Desktop Server on Windows and any rdp-client from Linux (rdesktop but there are others)
* UltraVNC on Windows - any VNC-client from Linux (vncviewer but there are many others)

Sadly, Windows doesn't natively support the remote windowing system used by most Linux desktops X/Windows. There are commercial versions, but those usually provide an X-Server, not the X-Client.

Going from Windows to Linux, there are other options that work and perform well - Spice and NX.
I wrote an article about all this here: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) that might explain a little clearer all the options. It is from the Linux view, of course.

Good luck. Feel free to ask more specific questions.

---

### Post by Skrimshaw on 2013-03-21
what i want to do is make my desktop do the heavy lifting for my laptop/ubuntu machine and i want to do it wirelessly ( i have decent internet 30mbps down and 15up) so i think my wifi could handle it and the only game i really want to play is ...... minecraft sad i know but its addicting anyways ill check out your links and hopefully one will do the trick thanks!

---

### Post by Bölvaður on 2013-03-21
When I saw the name of your thread I knew this existed and had been talked about slightly here on the forum (not sure how useful those threads are to you)

[http://www.streammygame.com/smg/index.php](http://www.streammygame.com/smg/index.php)

---

### Post by TheFu on 2013-03-22
> **Skrimshaw said:**
> what i want to do is make my desktop do the heavy lifting for my laptop/ubuntu machine and i want to do it wirelessly ( i have decent internet 30mbps down and 15up) so i think my wifi could handle it and the only game i really want to play is ...... minecraft sad i know but its addicting anyways ill check out your links and hopefully one will do the trick thanks!

If the graphics is slow, a remote desktop might work, but the redraws will probably suck. 50Mbps is nothing-nothing.  A video card has 5Gbps or more these days. You can't expect a relatively tiny pipe to handle so much data.  I have a gige wired network and can't stream video over a desktop in any acceptable manner.  Video plays back great, if I access remote files.

Anyway - take a look at my blog and try some of those things.  I think you will not be happy with the results.

---

### Post by linuxpenguin on 2013-05-04
How old is your laptop? I don't play Minecraft but according to the site it's Java-based and you can run it on Linux, they have a description right on the download page of what to do. And the system requirements are rather low, aside from the memory requirements... if you haven't already you might want to try just running it on your laptop.

[http://help.mojang.com/customer/portal/articles/325948-minecraft-system-requirements](http://help.mojang.com/customer/portal/articles/325948-minecraft-system-requirements)

---

