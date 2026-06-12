---
title: "Gnome file dialog very slow"
date: 2009-01-09
forum: General Help
---

### Post by bailout on 2009-01-09
Ex kde user trying to get used to gnome here. 

I am finding the dialog that opens when opening/saving a file to be very slow if there are many files in the folder it is opening. 

I was downloading some photos off flickr. After clicking save as the gnome file dialog appears. At first, on an empty folder, it was quick, however, after I had saveed a few files it started to take a long time to open and soon because unusable. I ended up having to dl 3 or 4 files to a temp dir and then move the files to the final destination so the temp file was empty again and repeat the process.

Is this slowness just a bug in gnome and is there anything I can do about it?

thanks

---

### Post by bailout on 2009-01-10
Nobody have the same problem?

---

### Post by wolf550e on 2009-02-25
I have the same problem. I'm looking into it. If I find something, I'll post it here.

---

### Post by danomatika on 2009-03-04
I had the same problem when reinstalling ... it seems the old tracker cache is slowing down the gtk dialogs for some reason.  I found [this Ubuntu forums post with the fix]("http://ubuntuforums.org/showthread.php?t=811795&highlight=open+save+issue&page=2").

Remove tracker and its config files, then restart:

```
sudo apt-get remove tracker --purge
```

Afterwards, you can reinstall tracker and it will generate a new valid cache.  I'm sure it would be better to just straight out remove the cache file directly, but I don't feel like hunting it down right now.

---

### Post by t.rei on 2009-03-23
Thanks, that worked.

---

### Post by ike on 2009-05-11
I tried removing tracker like danomatika suggests, but that didn't work for me. File dialogs are still slow in Gnome. It takes approximately 20-30 seconds for the file dialog to open when I press the Browse button in a file upload form in firefox (3.0.10).

I am running Jaunty.

Any ideas?

---

### Post by ike on 2009-05-11
My mistake! It turned out that the tracker processes was running in the background even though I removed the package. Now it works great!

---

### Post by mwillams73 on 2009-05-29
This didnt work for me at all, i removed and purged it as per the instructions and rebooted, same 1 minute to 2 minute hang of the save as dialogue box, i then reinstalled it and still it hangs. The folder in question is 311 mb's with each file inside it no more than 300 kb's in size each, so my question is why doesnt this work for me? Also as a half *** work around i have two folders now for this operation , one called vol 1 and the other called vol 2, I save the wallpapers in vol 2 and copy and past them to vol 1, the problem is when i copy them to vol 1 it takes forever and im talking up to 3 minutes for no more than 100 mb's as ive noticed after the folder reaches that size thats when it start to lag the dialogue box and also the copy paste, whats weird is i can copy a movie file of 700 megs to a folder that has 1 gig of videos in it and it actually takes less time then the 100 megs of files into less than 500 meg folder?  

So whats up with this, i cant figure it out, it did this in intrepid as well. Im running hardy cause so far its the only linux distro that hasnt fought me tooth and nail just to do simple things. Im running a gigabyte K-7 triton motherboard, AMD athlon 1.2 gh with on demand scaling to a stable 1.7 gh cpu,1 gig DDR ram, Nvidia 6200 LE-A with 256 ddr2 ram, a maxtor 250 gig 7200 rpm Hard disk. Thanks if you guys can figure this out for me! I really need this to work right im an artist and this is really, really cutting into my up time when i need to get things done.

---

### Post by Ubuntiac on 2009-06-08
I'm getting this too on:

Kubuntu Jaunty AMD64
ATI HD4850 + FGLRX
AMD Phenom II 3.6ghz quad core
4 gig DDR3 ram

Has anyone filed a bug on this issue? It sure makes normal computer usage tricky with Gnome apps...

Oh, and I *never* had tracker installed on this PC and have no tracker daemon running.

---

### Post by gradysghost on 2009-09-26
I managed to get things fixed (perhaps temporarily) by just killing all tracker processes.

```
pkill tracker*
```

Though you should probably make sure you don't have any unrelated processes beginning with "tracker" before you run that.

---

### Post by renkinjutsu on 2009-09-26
> **mwillams73 said:**
> This didnt work for me at all, i removed and purged it as per the instructions and rebooted, same 1 minute to 2 minute hang of the save as dialogue box, i then reinstalled it and still it hangs. The folder in question is 311 mb's with each file inside it no more than 300 kb's in size each, so my question is why doesnt this work for me? Also as a half *** work around i have two folders now for this operation , one called vol 1 and the other called vol 2, I save the wallpapers in vol 2 and copy and past them to vol 1, the problem is when i copy them to vol 1 it takes forever and im talking up to 3 minutes for no more than 100 mb's as ive noticed after the folder reaches that size thats when it start to lag the dialogue box and also the copy paste, whats weird is i can copy a movie file of 700 megs to a folder that has 1 gig of videos in it and it actually takes less time then the 100 megs of files into less than 500 meg folder?  

So whats up with this, i cant figure it out, it did this in intrepid as well. Im running hardy cause so far its the only linux distro that hasnt fought me tooth and nail just to do simple things. Im running a gigabyte K-7 triton motherboard, AMD athlon 1.2 gh with on demand scaling to a stable 1.7 gh cpu,1 gig DDR ram, Nvidia 6200 LE-A with 256 ddr2 ram, a maxtor 250 gig 7200 rpm Hard disk. Thanks if you guys can figure this out for me! I really need this to work right im an artist and this is really, really cutting into my up time when i need to get things done.

How much RAM do you have? i know nautilus caches icons into RAM and doesn't release it when it closes, causing high RAM usage.. i don't know if it has anything to do with this though..

also, i remember having this problem when i had NFS shares or SMB shares mounted even after the servers have been disconnected.

---

