---
title: "Kompozer and Shares"
date: 2009-03-03
forum: General Help
---

### Post by jaime256 on 2009-03-03
Hi. I have Kompozer installed and I use Screem for most of the editing. I would like to use Kompozer, but I was wondering if anyone has any idea on how to open share files from within Kompozer? The share is a nas and the desktop is Ubuntu 8.10. I noticed this same thing with the previous versions too. I can copy files to my locad desktop, but I rather just point to them as in Screem. There's just no option in there so I hope that maybe I'm just missing something. Any help is appreciated. Thanks.

---

### Post by SteveDee on 2009-03-03
> **jaime256 said:**
> Hi. I have Kompozer installed and I use Screem for most of the editing. I would like to use Kompozer, but I was wondering if anyone has any idea on how to open share files from within Kompozer? The share is a nas and the desktop is Ubuntu 8.10. I noticed this same thing with the previous versions too. I can copy files to my locad desktop, but I rather just point to them as in Screem. There's just no option in there so I hope that maybe I'm just missing something. Any help is appreciated. Thanks.

If your problem is that the option "network" does not appear in the "File" > "Open File" dialog, then take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1009901](http://ubuntuforums.org/showthread.php?t=1009901)

---

### Post by jaime256 on 2009-03-03
Thanks for the link SteveDee and to the others who posted the info that got me to write these steps. I like to stay away from the CLI as much as possible, just because I hate to type so after reading that post I came up with some simple steps for others that don't want to do the CLI part too much. You still need to follow a few steps, but hopefully this will help.
Here you go...

Steps:
1. Log in to your shares the way you normally do. This will add the share to the .gvs folder which is empty if you haven't logged in. Remember this is a hidden folder in your home directory.

2. Under the .gvs directory right click on the folder for your share and choose the "Make a Link" option. This creates a link to the share.

3. You can now open Kompozer or whatever application that normally can't browse the shares, and now you will be able to browse the "Link" for the share or shares that you created. The linked share now appears on your file/browse area of your application. Just remember where you created the link. You can now edit/browse your files from within the program. Nice.

4. The other option is to just use the link to browse your files instead now, it doesn't matter. I just left the link where it was created which is the home directory.

Note: If you log out, the link is broken, but all you need to do is log back into your shares and it works again. The link won't get deleted unless you click on it first before loggin into your share, but I just did a refresh after login in and it works again. I rebooted my computer just to test this out. If it gets deleted, just create one again.

I do have one question, is the link created the same thing as a sym link? I'm not sure but I'm just curious.

---

### Post by jaime256 on 2009-03-03
Problem: I just found out that the program will just close on me when I try to go to the toolbar and do a bold or anything up there. I have no idea why, but the instructions for browsing do work. Now if someone can tell me why the program just closes that would be cool. I think it may be a bug just like Screem used to have. Yes, it used to close on me for no reason too but that got fixed. Either way I hope that gets fixed so we can use it.

I haven't tried it with any other programs because this was the only one that I needed. If anyone can test it with something else and let us know whether it works or not, that would be great. Thanks.

---

### Post by dcstar on 2009-03-03
> **jaime256 said:**
> Problem: I just found out that the program will just close on me when I try to go to the toolbar and do a bold or anything up there. I have no idea why, but the instructions for browsing do work. Now if someone can tell me why the program just closes that would be cool. I think it may be a bug just like Screem used to have. Yeah, it use to close for no reason too but that got fixed. either way I hope that gets fixed so we can use it.

I haven't tried it with any other programs because this was the only one that I needed. If anyone can test it with something else and let us know whether it works or not, that would be great. Thanks.

Kompozer in 8.10 is broken:

[http://ubuntuforums.org/showthread.php?t=988682](http://ubuntuforums.org/showthread.php?t=988682)

---

### Post by SteveDee on 2009-03-04
> **jaime256 said:**
> Problem: I just found out that the program will just close on me when I try to go to the toolbar and do a bold or anything up there. I have no idea why, but the instructions for browsing do work. Now if someone can tell me why the program just closes that would be cool. I think it may be a bug just like Screem used to have. Yeah, it use to close for no reason too but that got fixed. either way I hope that gets fixed so we can use it.

I haven't tried it with any other programs because this was the only one that I needed. If anyone can test it with something else and let us know whether it works or not, that would be great. Thanks.

Kompozer V1:0.7.10 is broken, and I think that is still the offering from the Intrepid repository.

I took some advice and installed direct from: [http://kompozer.net/zip/](http://kompozer.net/zip/) and its been working with no problems. I have version 20081218. Just download and unzip to your home directory (no install required), and run the "kompozer" file.

This does not appear to work for everyone, see: [http://ubuntuforums.org/showthread.php?t=967887&page=4](http://ubuntuforums.org/showthread.php?t=967887&page=4)

---

### Post by jaime256 on 2009-03-04
Thanks guys. I'm glad it wasn't just me. I'm also glad this will help others too. Dcstar, I have yet to try the other options, but I got a test to study for right now so I will try something later.

---

### Post by jaime256 on 2009-03-05
Okay some good news, I downloaded one of those other versions 0.7.99(20081118) and that seems to work for me as well. The program doesn't close anymore so even though you still have to go through all the steps, at least now I have one more program that I can use. And again, Thanks SteveDee for the links! I just checked to see what version was closing on me and it's version 0.7.10(20080314). Go figure.

---

### Post by SteveDee on 2009-03-06
> **jaime256 said:**
> Okay some good news, I downloaded one of those other versions 0.7.99(20081118) and that seems to work for me as well. The program doesn't close anymore so even though you still have to go through all the steps, at least now I have one more program that I can use. And again, Thanks SteveDee for the links! I just checked to see what version was closing on me and it's version 0.7.10(20080314). Go figure.

That looks like a qualified success, but what are "...all the steps..." that you refer to?

---

### Post by jaime256 on 2009-03-08
Just the steps I wrote above on one of the postings so you don't have to open up a terminal window and that will allow you to edit files on a nas share without having to make a local copy. And yes, I finally got the program to open my site, but unfortunately when I tried editing it, it kind of messed the thing up so I may have to just leave that for the rest of the pages and not the main page. At least for now or until I can figure out why it does what it does. Other than that, I just feel all warm and fuzzy now that I can use this for something. :)

---

