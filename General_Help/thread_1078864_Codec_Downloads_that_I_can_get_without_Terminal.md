---
title: "Codec Downloads that I can get without Terminal?"
date: 2009-02-23
forum: General Help
---

### Post by Spirte on 2009-02-23
Well, to start, I'm very new to Linux and still in the process of learning what I've already got, and what I need.

Now, I should also state that I've got a REALLY small download limit with my ISP.  

Anyways, I'm trying to watch movies that I saved when I transferred from Windows.  They're in .wmz, .avi, .mpeg, and all the other common formats.  Unfortunately, as of now, I can't play them.  I've gone to friend's houses to try and download codec packs with their internet, but unfortunately, the only downloads I can find involve the use of terminal.  All my friend's are running Windows.  

So the point I'm trying to get to - How can I get the codecs I need and possibly another good video player, like VLC?

Also, if I'm just completely missing something, and there's a way to run these files without downloading anything, let me know.

THANKS.

---

### Post by howefield on 2009-02-23
You could get your friends to download the packages and then save them to a memory stick, cd or whatever.

In synaptic find the packages you want and just before you click apply to install them , check the box that says "download package files only"

---

### Post by cariboo on 2009-02-23
If you go [here]("http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras"), you can download most of the codecs you need to play most audio/video media. To play dvds, you need libdvdcss2 which is in the [Medibuntu]("http://help.ubuntu.com/community/Medibuntu#Adding the Repositories") repositories. Follow the instructions on the page for your version. It's only a 37k download, so it should effect your download totals to much.

Jim

---

### Post by mb_webguy on 2009-02-23
Generally, anything you can download and install using the terminal, you can download and install using a GUI.

Open System->Adminstration->Software Sources, and go to the Third-Party Software tab.  Click the Add button, paste the following line in the textbox, and click Add Source.```
deb http://packages.medibuntu.org/ intrepid free non-free
```Now open System->Administration->Synaptic Package Manager.  Search for "medibuntu", find the medibuntu-keyring package, mark it for installation, and click the Apply button.  Now click the Reload button to update your sources.

Now you need to search for and install the following libdvdcss2 and non-free-codecs packages.  These two packages are only about 250KB in total, so I don't think your ISP's download limitations are going to be a problem.

---

