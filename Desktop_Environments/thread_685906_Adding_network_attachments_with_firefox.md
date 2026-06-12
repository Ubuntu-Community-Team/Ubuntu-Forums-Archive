---
title: "Adding network attachments with firefox"
date: 2008-02-02
forum: Desktop Environments
---

### Post by AgentZ86 on 2008-02-02
Hi

How to add attachments on the network with firefox

Basically when using webmail or yahoo etc. I can't browse to my files on the network to add them as and attachement.

My network connections and shortcuts on the desktop are working fine, but there is not options to browse network or anyplace else to add these files as an attachement.

Basically I can only browse the local files, and in my places there is no option for browsing the network or desktop server connections when I try to add attachments.

I hope this makes sense, but this is very annoying cause all my files are on the network and I can access them with connect to server shortcuts on the desktop or browse with nautilus, but not with any webmail applications etc. basically nautilus network features seems to disappear when you want to send an attachement and browse to that file on the network.

Please describe how to fix this.

Thanks

---

### Post by ayoli on 2008-02-02
> **AgentZ86 said:**
> Hi

How to add attachments on the network with firefox

Basically when using webmail or yahoo etc. I can't browse to my files on the network to add them as and attachement.

My network connections and shortcuts on the desktop are working fine, but there is not options to browse network or anyplace else to add these files as an attachement.

Basically I can only browse the local files, and in my places there is no option for browsing the network or desktop server connections when I try to add attachments.

I hope this makes sense, but this is very annoying cause all my files are on the network and I can access them with connect to server shortcuts on the desktop or browse with nautilus, but not with any webmail applications etc. basically nautilus network features seems to disappear when you want to send an attachement and browse to that file on the network.

Please describe how to fix this.

Thanks

firefox and others browsers (even IE) don't handle other protocols (ssh, samba, ..) so it is not possible to rowse your network files afaik

---

### Post by AgentZ86 on 2008-02-02
> **ayoli said:**
> firefox and others browsers (even IE) don't handle other protocols (ssh, samba, ..) so it is not possible to rowse your network files afaik

Thanks for the response.

Firefox on windows has no problem with this, and also firefox on kde can browse to network locations.

However, this is not really firefox as the basic file browser opens in this case.

I hope I'm making this clear. I don't want firefox to browse to anything really, however I don't believe it's actually firefox that is opening when you download something and a window opens to ask where to save to. In this case it's probably nautilus. Or another scenario is when you want to simply add an attachment in web mail, in which you click browse, and a file browser opens and you can browse to the file which you wish to attach. I would think it is nautilus, but it's strange cause when this browse portion opens, the features for network or if you select places in that particular menu, the network browse option is not there, nor is the desktop shortcuts for my connect to server short cuts. Any such feature that could give me access to my network files does not exist. 

The question is why?? and how to fix it.

Why not gnome, I've not had this problem with other distros, Linspire could browse to my network when I wanted to lets say download something and save to network location or also I could open files on the network and the associated program would work. So far on ubuntu I can open the open office files and open office will open as it should, and also any html files of course the firefox browser will open or perhaps I can open with nautilus, but it's a pretty basic feature I'm looking for I'm not sure why this is not available or seems to be somewhat evasive. 

But the main most important thing to me is to be able to send attachments with webmail. I don't want to have to open nautilus, then go to my connect to server shortcut, then open my network folders then find the file, then copy to my desktop, then I can select browse from within webmail then browse to my desktop and attach the file, then delete if from my desktop.

I mean that is a real pain and what are you suppose to do with your network actually if you can't browse to it so save files, you can't (save as) to the server or network with applications your working on. You have to save to local folder, then either cut and copy from the local location, then browse the network with nautilus and paste to your network. You can't open files on the network with open with commands, well only limited use and only on some programs. Networking is almost useless this way.

You should be able to add an attachement in webmail without having to browse to the location then having to copy the files to the desktop in order to attach the file. And what if your sending a 100mb of pictures or so, you now have to wait for the files to transfer from the server to your desktop or local folder then send/attach to your webmail.

I have this problem when trying to add pictures to ebay also. I put the pictures on the server, then can't add them to ebay because the stupid file browser that opens won't let me browse to the network to add the file. So I have to copy again to the desktop, then I can add the images to ebay, then delete from the desktop.

What a merry go round this seems to be.
Are you sure there is not something else to fix this, it seems like such a simple feature that anyone with a business uses all the time.

Well that all I know, I wish I could make this work.

---

### Post by AgentZ86 on 2008-02-02
I'm slowly learning that this part of the vfs in gnome really stinks.

I want network transparency and it appears I have to learn how to install and use fuse, and perhaps gfuse to mount these network folders correctly so that all programs can see them in ubuntu.

What a pain. I still love my ubuntu computer, but just wish I could get this worked out.

---

