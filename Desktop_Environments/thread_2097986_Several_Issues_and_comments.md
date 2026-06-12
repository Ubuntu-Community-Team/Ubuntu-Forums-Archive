---
title: "Several Issues and comments"
date: 2012-12-25
forum: Desktop Environments
---

### Post by HalinQuincy on 2012-12-25
So, I've been visiting and leaving various flavors of Linux (including Ubuntu) for roughly 12 years now. I currently have just installed Ubuntu 12.04 LTS and at first glance it seemed that (at least Ubuntu) was ready for prime time or close to it. So far, the desktop guide doesn't seem to offer more info than what I can readily intuit and could not lead me to the answers I sought.  But, perhaps I'm missing something.  I'm actually hoping that is the case. So, I hope you won't take too much offense at my recount of frustrating experience.

I've installed to a box with a P4 3.06 ghz w/HT, 2mb cache. 2 Gig of ddr 667 ram. I figured this should be plenty for Ubuntu Desktop.

Issues:
1) Hardware:
I installed Ubuntu to an ATA drive hanging off the motherboard. After I was somewhat confident of the installation, I added a 3ware Escalade IDE Raid card w/ 2 drive attached. Just about every distro of Linux I've tried automatically recognized the controller and the drive attached thereto. For the life of me I can't find anything that tells me how to get new hardware recognized and installed.
2) Printers:
My networked Epson Workforce 545 was handily recognized and installed by just entering the static IP I had assigned to the printer. Not so straight forward for the Epson Artisan 50 I have connected to a Netgear PS121 (again on static IP). Non of the advice I could find on the forum of by Google seemed to work. I finally tried entering the IP and Port from the Windows 7 printer dialog. Oddly enough 172.16.1.21_1 worked. The real bear was my Canon PIXMA MX700. Ubuntu seemed to see it but no matter what I did it wouldn't print. I finally found a reference to the BJNP backend for canon printers that could be got from source forge. After d/ling the package I tried to make sense of the installation directions to no avail. So, I installed Turboprint trial (which also automatically installs the very same bjnp stuff). As I started to get turbo print to recognize the MX700 I could see in the dialog what the device URI needed to be.
So I closed Turboprint and ran the native add printer dialog, entering the appropriate URI. Worked a treat. It just seems odd that a) with all the numerous posts in the forum tagged MX700 none mentioned the bjnp package that was needed. That package doesn't seem to show up in Ubuntu Software center and no hits on a search of Canon MX700. Someone should do a stickie  on the bjnp package with a tag for canon printers. Better yet it should be installable fron the software center.
Oh and just BTW, advising to purchase HP junk just because 'the drivers just work” is a non starter.
3) So now that I don't need Turboprint I go to uninstall and gee whiz it got installed through what I thought was the software center (I remember seeing the option to do so, pretty sure I clicke yes), but doesn't show up anywhere to do an uninstall. I finally found how to uninstall in the Turboprint forum. Got that done
This is still tooooo much like hunting snipes when trying to get simple maintenance done.
4) The Unity GUI is about as awkward and counter intuitive as I've seen. It's way too sparse, though it is pretty <g>. When you resize a window in say system settings/ printers->-> nothing stays that way the next time you go to open anything. At high resolution on a 24” screen, constantly adjusting window size gets old real fast.
The file manager is almost useless.  There is no directory tree view, so when you do a search to find a file you get an icon on the page but no reference to where it's located. There doesn't seem to be a way to ditch icons and simply have a list view.  There doesn't seem to be any logic to how installed applications are listed in the dashboard. The pdf viewer doesn't have word-search capabilities. Search in desktop help doesn't seem to work.
5) I've got a MS wireless mouse. I didn't expect that the native Ubuntu drivers would support more than a standard wheel mouse. Nor did I expect the mouse to be all herky jerky, especially when used to scroll in Firefox. Or maybe this is a firefox problem.
6) I can't seem to get permissions to edit the hosts file. Can someone give me the command line with the correct syntax to open and edit hosts.

There is other stuff that I found underwhelming, but I've worn myself out already <G>.
I've been trying to dump windows for 12 years now (and I don't mean “get a Mac”). So I'm really hoping that there are fixes for what I've listed or better yet, that I'm just plain wrong and you all can show me the errors of my ways <g>.

Kudo's:
             Ubuntu locked up and I had to do a hard reset. I hadn't saved this post and I was pleasantly    surprised to watch the system recover the work in LibreOffice Write.

All your assistance and patient forbearance most appreciated.

Mahalo Nui Loa,
                               HalinQuincy

---

### Post by 2F4U on 2012-12-25
> 4) The Unity GUI is about as awkward and counter intuitive as I've seen.

This has been discussed extensively. If you don't like Unity, there are plenty of alternatives in the Ubuntu repositories.

> 6) I can't seem to get permissions to edit the hosts file. Can someone  give me the command line with the correct syntax to open and edit hosts.

How did you try to edit the file? One method that should work is, open a terminal and type

sudo nano /etc/hosts

or

gksudo gedit /etc/hosts

---

### Post by offgridguy on 2012-12-25
> 

I've been trying to dump windows for 12 years now (and I don't mean “get  a Mac”). So I'm really hoping that there are fixes for what I've listed  or better yet, that I'm just plain wrong and you all can show me the  errors of my ways <g>.

I came to ubuntu/linux hoping for a replacement for windows,  I now realize that
for _me _that was an unrealistic expectation.  I now use both, quite happy with that.:)

---

### Post by HalinQuincy on 2012-12-30
Sorry for the delay in replying.
 
:smile:> **2F4U said:**
> This has been discussed extensively. If you don't like Unity, there are plenty of alternatives in the Ubuntu repositories.
 
I thought it might have garnered more than a few comments :). So, is there a fair evaluation / comparison of Unity and the alternatives? 
 
> **2F4U said:**
> How did you try to edit the file? One method that should work is, open a terminal and type
 
sudo nano /etc/hosts
 
or
 
gksudo gedit /etc/hosts
 
Well, first I tried to edit hosts in a text editor. then I tried sudo edit /etc/hosts which of course didn't work. Thanks for the suggestions. "nano" worked fine. Didn't try gksudo since nano worked. is gksudo gedit in a seperate batch of commands? 
How can I get a list of what commands are installed with use syntax. Other commands, tools & utilities that might be worth installing & learning. I just cobbled together a little file server w/ 4 drives on SiI 3124 0+1 raid array. installed Ubuntu 12.04.1 Server - amd64. Now I see Server is ALL comand line for config and maintanence. Sokay :). I guess I've just committed myself to a command line strategy.
 
Mahalo

---

### Post by HalinQuincy on 2012-12-30
> **offgridguy said:**
> I came to ubuntu/linux hoping for a replacement for windows, I now realize that
for _me _that was an unrealistic expectation. I now use both, quite happy with that.:)
 
 I think I have to agree with that conclusion.

---

