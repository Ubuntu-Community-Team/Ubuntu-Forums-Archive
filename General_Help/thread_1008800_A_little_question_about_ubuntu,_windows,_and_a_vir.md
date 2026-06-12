---
title: "A little question about ubuntu, windows, and a virus."
date: 2008-12-11
forum: General Help
---

### Post by zero1221 on 2008-12-11
My question is all tho really silly because I think I know the answer to it.
If I use ubuntu to save my files from my a virus that has ravaged my
windows computer will that virus still be able to copy itself even if I'm
using ubuntu to save the files? I'm pretty sure viruses aren't cross platform and ubuntu is pretty safe because it doesn't let everyone do admin stuff if I remember right. This is my last desperate attempt to save my files before I have to regrettably restore my windows system to purge it
of the virus if that will even be possible because I think it may of destroyed my recovery partion that this factory made hp computer has instead of disc.

---

### Post by basnetwork on 2008-12-11
I am no expert on this but I'll take a shot at this.

I recently moved a few computers from windows to ubuntu as they had some virus issues on windows.  

I setup a ubuntu server and installed Clam AV on the new server and moved all the files from the windows boxes over to the server. During a scan of the infected files, it did find some virus signitures; however Clam was able to clean them. Most of the files I moved to the server were office docs, pictures, and mp3s. 

There is one last windows box on the network, and using that computer to open the files that Clam cleaned on the server gave no problems.  Double checking the files with AVG on the windows box showed the file were clean.

I'm not sure if this info is of any help to you, but you might find something in there you can use.

If you do happen to be with out your recovery partition, maybe now is a good time to make the switch to Ubuntu or another Linux distro and put all the virus problems behind you.  Just my $.02

Hope this helps and best of luck to you.

BAS

---

### Post by TeXtonyx on 2008-12-11
virus are just about never in data files such as mp3 and images.
Usually they are in Windows registry. But they can be in emails
so that if you had an infected message in Thunderbird (email) in
Windows and you used Thunderbird in Ubuntu and imported the bad
file into the Ubuntu Thunderbird, I'm not certain you would be
safe. Likewise if you saved an infected MS Office Word file in the 
.doc format and then imported that file in OpenOffice Writer, I'm
not sure that is entirely safe. There are some virus and trojans
which attack Linux; I've never heard (yet) of a cross-ported virus
that would infect either Linux or Windows if it were downloaded
and executed. It seems like it would have to target (if it existed)
a cross-platform application.

---

### Post by Zerocxis on 2008-12-11
The virus should not run because it is mainly a windows binary. It might try to run fruitlessly in Wine if you have it installed but it will (edit: read - should) not do any damage because Wine operates in the user environment, not in the root environment. Just make sure you don't copy the virus as you are moving your files from your Windows install to your Ubuntu install. 

Hope this helps,

Zerocxis

(edit) But then again I am no expert either, so ymmv.

---

### Post by noerrorsfound on 2008-12-11
> **TeXtonyx said:**
> virus are just about never in data files such as mp3 and images.
Usually they are in Windows registry. But they can be in emails
so that if you had an infected message in Thunderbird (email) in
Windows and you used Thunderbird in Ubuntu and imported the bad
file into the Ubuntu Thunderbird, I'm not certain you would be
safe. Likewise if you saved an infected MS Office Word file in the 
.doc format and then imported that file in OpenOffice Writer, I'm
not sure that is entirely safe. There are some virus and trojans
which attack Linux; I've never heard (yet) of a cross-ported virus
that would infect either Linux or Windows if it were downloaded
and executed. It seems like it would have to target (if it existed)
a cross-platform application.
The registry doesn't hold executable files, so how could a virus be there? And what's with the line breaks?

---

### Post by zero1221 on 2008-12-11
Thank you everyone this has all been a big help. I'm pretty sure it's
just infected the os (no thanks to my countless anti programs) and it's
good to know that the virus isn't still running because it was a nasty one
that stopped all my anti programs from working properly and prevented me from even getting it in safe mode. I think I might try to get a dual boot system running sometime soon because I really like linux from the flavors I've tried, but still need windows for my parents and sister who have a lot of programs that only work in windows. Thanks again

---

### Post by albinootje on 2008-12-11
Here's a funny and interesting article about testing MS-Windows-viruses with Wine in Linux : 
[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

And about your parents and sister needing a lot of windows-programs.
If your machine is pretty recent you really should try VirtualBox and have Windows running in that.
Use the virtualbox-ose package in Ubuntu, or if you want more features, use the closed-source version of VirtualBox :
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
GL!

---

### Post by lisati on 2008-12-11
> **TeXtonyx said:**
> virus are just about never in data files such as mp3 and images.
Usually they are in Windows registry. But they can be in emails
so that if you had an infected message in Thunderbird (email) in
Windows and you used Thunderbird in Ubuntu and imported the bad
file into the Ubuntu Thunderbird, I'm not certain you would be
safe. Likewise if you saved an infected MS Office Word file in the 
.doc format and then imported that file in OpenOffice Writer, I'm
not sure that is entirely safe. There are some virus and trojans
which attack Linux; I've never heard (yet) of a cross-ported virus
that would infect either Linux or Windows if it were downloaded
and executed. It seems like it would have to target (if it existed)
a cross-platform application.

I have encountered malware (viruses etc) in mp3 files - not often, but enough to know to be careful. Usually this has been through files I've obtained through software like frostwire/limeware. Happily, my Ubuntu box hasn't been hurt by any.

---

### Post by Zerocxis on 2008-12-12
I will say that there are some malware out there that are disguised as mp3s, even if you have Windows set to show known files types. They are zero length files that actually contain a bootstrapper that links to the default web browser to take you to a site that either does a prompt that even if you click no to downloads the payload or does a drive-by-download. So, be careful when downloading such files. 

Zerocxis

---

