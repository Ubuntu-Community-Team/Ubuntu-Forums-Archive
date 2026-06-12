---
title: "How to transfer desktop and mail settings to new *smaller* drive"
date: 2014-08-06
forum: Desktop Environments
---

### Post by BZFlagLEGOManiac on 2014-08-06
I recently purchased a new 120GB solid state drive to replace my 1TB hard disk which was getting full. I copied all my photos, videos, and documents to an external network drive and I'm not installing a lot of the software I had experimented with over the years on the old system, but stopped using along the way.

I began by installing lubuntu 14.04 to the SSD, then mounting the old 1TB drive and booting from it.

Scanning previous posts on the subject of migrating to a new hard disk, I tried to follow the advice:

- from the /home/username directory I copied the non-hidden files in the root folder, the Desktop folder, and the hidden folders: .config, .cups, .kde, .local


I then booted from the SSD, but the text for the login screen was incredibly tiny. On my desktop, the files were there, but the text was tiny and the spacing between icons was huge. When I tried to re-align it via the "sort files" context menu, which re-arranged the files but kept the spacing. I then moved the icons manually into a smaller cluster after which "sort files" does absolutely nothing. It's as though manually moving them locks them in position.

On the plus side, my upper and lower panels were arranged the way I originally had them vs. the lubuntu default, so some settings did, in fact, get migrated over.

What I had expected was that my original icon spacing and original text size would have been preserved. I've been able to change the text size of the desktop icons separately, but the icon spacing problem still exists. Text within windows, in menus, and in tabs is still incredibly small.

Lastly, and very important, is kmail.

I had read somewhere that kmail stored everything in the .kde directory but all I got was my account settings and none of my previous mail folders.

Reading elsewhere I learned that the copying had to be done as root because, while the usernames are the same on the old and new systems, the user IDs will be different. I therefor logged in the the original hard disk, mounted the SSD, opened a terminal and typed "sudo pcmanfm" to start a file manager as root. I them dragged and dropped the same folders onto the SSD with the same results.

Can anyone tell me what folders I need to copy over to get the same desktop settings (text, icon spacing, resolution), as well as my mail? BTW. With respect to kmail, I tried it's import/export function and got nowhere, only to later read that people have been complaining about the broken import/export for years.

LEGOManiac

---

### Post by TheFu on 2014-08-07
I would grab everything under /home and just leave all the media files (images/audio/video) behind.

---

### Post by Rob Sayer on 2014-08-08
+1.  Not all those user settings are necessarily where you'd expect at first.

---

### Post by BZFlagLEGOManiac on 2014-08-14
OK, so I answered this thread and apparently must have forgotten to click 'Post'.

Anyway, my core problem is that I used the old installation of lubuntu to experiment with. As a result, there are a large number of packages that were installed that I no longer use. Some I removed, but forgot to 'completely remove' and, hence, there are directory entries in my home folder for them. I'm trying to start over  with a clean slate which is why I don't want to grab everything in my home directory.

I moved my media files off to a network share.

The only four things that are still outstanding are:

1) The desktop icon spacing and the text sizes of all icons, windows titles and tabs system wide. I have a distant recollection of having to use some tweaking utility a long time ago to get it the way I want it. I have poor eyesight so I definitely need larger text. My expectation was that copying the .config folder over from the old system would have set everything up the way I like it. It worked for the location and contents of panels but did nothing for the desktop and folder settings.

2) I had expected my four printers to be set up by copying the .cups folder, but apparently not.

3) My biggest problem is finding my KMail mail stores. Copying the .kde folder gave my my mail account settings so with the passwords, I am able to read current mail but I normally remove the mail from the POP3 server  when I download it, so I'm needing to recover all that history.

4) Lastly, the login screen text is tiny. Currently, I'm the only user so it's obvious whom to pick, but once the rest of the family accounts are set up, I'll need to be able to read this. Since the login screen is not part of any individual profile, I would not expect to find it's configuration settings in my home folder but I have no idea where it would otherwise be.

Nor do I have any idea what utility I used way-back-when to do all this configuration in the first place.

---

### Post by TheFu on 2014-08-14
**I would still grab everything under /home and just leave all the media files (images/audio/video) behind. **

If you like, move those files to a different directory/account and start fresh with a new account, then selectively move the files over 1 at a time and test.  It is likely that will take weeks.   I would NOT be very picky, since my time is worth more than 50MB of old config files that don't matter. It just isn't worth it to me.

Those configuration GUIs ... just modify text files on the system.  If they are personal settings, that is under your $HOME. If they are for the entire system (sudo is required), the settings will be under /etc/.

Printers sometimes have drivers which must be built, linked, and installed. Sometimes not, but many times yes. That is likely what happened to yours.

Sorry - I don't know anything about KDE. Haven't touched it in 10 yrs.

---

