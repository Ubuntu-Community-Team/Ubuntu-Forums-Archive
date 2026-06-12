---
title: "backup thunderbird emails? (Solved)"
date: 2005-10-13
forum: Desktop Environments
---

### Post by bionnaki on 2005-10-13
I am about to install a fresh copy of breezy. just wondering if anyone knows how to backup my thunderbird emails. thanks!

---

### Post by aysiu on 2005-10-13
It's a hidden file--either /home/username/.mozilla-thunderbird or /home/username/.thunderbird.

Press Control-H to show hidden files.

---

### Post by bionnaki on 2005-10-13
ok, I see the hidden directory...but what files should I backup?

---

### Post by louiscyphre on 2005-10-13
You can backup the entire "/home/username/.mozilla-thunderbird" folder, install a fresh copy of breezy and thunderbird, run it the first time (thunderbird creates a new .mozilla-thunderbird folder), close thunderbird and replace the new folder with the old one and... thunderbird will be *exactly* as it was before.

...you can do the same with firefox (/home/username/.mozilla) ;)

Good luck! :)

---

### Post by Jad on 2005-10-13
also there is an extension allow you to import/export emails and accounts settings

---

### Post by mrmcctt on 2005-10-13
What about bringing mail folders fro windows to ubuntu?  I moved them from windows to ubuntu and all I got was the folders, not the e-mails in the folders.

---

### Post by Jad on 2005-10-13
Thats why I suggested using the extension, as you can import/export from windows/linux

---

### Post by yesplease on 2005-10-20
Ofcourse the import and export options in thunderbird are the best solution. 

When ubuntu is broken and you can not boot it, you can try to backup mail and other files with explore2fs from windows.

You can try to restore Grub to get into windows, or use the rescue mode on the windows CD with the option fixboot and fixmbr.

---

### Post by ProPilot on 2005-10-20
I was using Thunderbird then I discovered Evolution. I would like to export the files from Thunderbird to Evolution, however, my Thuderbird does not have an export function and my Evolution has an import function but will not import Thunderbird files.

How do I go about doing this?

Thanks

---

### Post by gw90se on 2005-10-20
I went thgrough this. I am not sure whether this is the fastest way, but it worked for me. Make new mailboxes in Thunderbird, but make them as a mbox file. Transfer messages to this box. You can then import this mbox to Evolution.

---

### Post by ProPilot on 2005-10-20
Thank you I looked in Tbird but I do not know how to do as you have suggested would you be kind enough to expand on how to do this.

Thanks

---

### Post by gw90se on 2005-10-20
I actually found an easier way to do this while I was trying to refresh my memory. Open Thunderbird and create a new folder. Let's call it "Transfer". Copy all of your mail messages to it. You can do this one at a time for multiple folders or create multiple folders if you need to. Open a file browser in your home directory and set it to show hidden files. Browse to .mozilla-thunderbird/(your profile directory).default/Mail/Local Folders/

You will see folders and also some files. You should see Transfer.msf and a file call Transfer with no extension. Copy the file with no extension. Browse back to your home directory and then go to .evolution/mail/local/

Paste the file here. 

Open Evolution and you should see your new folder has all the messages in it.

---

### Post by aysiu on 2005-10-20
When I migrated, I just copied

C:\Documents and Settings\username\Application Data\Thunderbird

to

/home/username/.mozilla-thunderbird

and everything was good.

---

### Post by ProPilot on 2005-10-20
gw90se

Thank you it worked - fantastic!

---

### Post by quill3033 on 2008-06-30
ok at work i was able to copy emails from outlook to regular folders on the server so others could read them - it was e-filing or something like that. I've tried to do this with Thunderbird and Evolution without success. 
I have been able to 'save as' and save files to  folder on the desktop - but I have to name every single email. And when I open the file it has way too much info - not very printer friendly... 
Anyone know how to do this? 
Also, let me know if I need to start a new thread ... as this is related to the topic but not exactly the same thing you have all been talking about.

---

