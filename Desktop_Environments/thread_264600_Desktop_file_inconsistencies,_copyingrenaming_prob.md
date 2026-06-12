---
title: "Desktop file inconsistencies, copying/renaming problems"
date: 2006-09-24
forum: Desktop Environments
---

### Post by ropers on 2006-09-24
First of all, apologies in advance, but I'll have to rant a bit. You know. That deeply cleansing feeling. Yadda, yadda, yadda.

I recently dragged some links from Firefox to the 6.06 Ubuntu Desktop (i.e. I dragged the favicons to the Desktop). 
One of the files was named:

   **217.157.2.18 - \extSupport\webswdb\786 Drivers\786LCD-5.25 Linux\.desktop**

Today I tried to back up all files on my Desktop to another partition (FAT32 format). When dragging the files, I got an error message.

First gripe:
This is the error message I'm getting:

[IMG]http://ropersonline.com/downloads/ubuntu-file-copy-error.png[/IMG]

This is not very verbose and DOES NOT GIVE ME THE FILENAME of the file that the copy operation fails on. Ok, it does, but it abbreviates the path/filename and that name CANNOT BE FULLY DISPLAYED at this point. I cannot resize the window and even copying and pasting the filename only copies this abbreviated version.

Upon finding out which file the message actually referred to (which wasn't easy because of the aforementioned issue), I guessed that the filename with its apparently FAT32-non-digestible characters was the problem (even though the impressively precise error message certainly didn't tell me).
So I renamed the file to:

  **link to 217.157.2.18 - Drivers 786LCD-5.25 Linux**

I did this right on the Desktop by right-clicking Rename.
However, the copy operation still failed with the same error message.
I then dropped to the Terminal shell and found that the file still had its old name!
So in the GUI, in GNOME, on the Desktop the file name shows as the latter and at the command prompt the file name still shows as the former. I rebooted, but things are unchanged. 

I then made a copy of a similar file at the CLI. Its name is:

  **SiS\XGI graphics drivers :: Index.desktop**

and the copy was named:

  **SiS\XGI graphics drivers :: Index.desktop.bak**

I then tried to rename that copy in the GUI to

  **SiS XGI graphics drivers  Index.desktop.bak**

and couldn't -- the new name was not being accepted in the GUI -- it just reverted back without any error message. I should add that with all of these files, I am the owner and I have read/write permissions to them.

At one stage a copying attempt even made the similarly named copy (minus the special characters) disappear, but I could not subsequently reproduce this.

On a related note, how do I fsck the root partition? When I tried this, it wouldn't let me -- because it couldn't get exclusive access (that's understandable) BUT I couldn't even find a way to schedule an fsck for the next reboot. I didn't seem to be able to do this in System -- Administration -- Disks (which is where I would expect this) and couldn't find anything in the man pages (which are probaly way over the head of the average nontechnical Ubuntu switcher). 

So these things, this inconsistent behaviour with file names and the way I couldn't even seem to do basic troubleshooting in Ubuntu is almost a showstopper for me. 
But I thought, fair enough, I'm used to trrouble and I've only used Linux for a week or so, so instead of wiping Ubuntu off my HDD, why don't I try the forums? 
That said, all of this does not at all compare favourably vs. my prior experiences with OpenBSD, Mac OS, Mac OS X, DOS and even Windows. I wish I could end on a higher note, but I'm pretty frustrated here. Hopefully something good will come out of this anyway.

Thanks for your attention. :)

---

### Post by CatKiller on 2006-09-25
.desktop files are a bit freaky. The name that gets displayed is encoded internally, and may well be different from the name.desktop of the actual file. Possibly when you're renaming the file through the GUI, it's just the internal name that you're changing. It seems I need to go look at hats, so I can't elaborate further. Sorry.

---

### Post by ropers on 2006-09-25
Wow. You're right. This is what I found when I looked inside one of the said files with **vi**:

Its file name displayed in the GNOME GUI is:

[INDENT]**link to 217.157.2.18 - Drivers 786LCD-5.25 Linux**[/INDENT]

while its file name as seen on the command shell is:

[INDENT]**217.157.2.18 - \extSupport\webswdb\786 Drivers\786LCD-5.25 Linux\.desktop**[/INDENT]

and its content is:

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=link to 217.157.2.18 - Drivers 786LCD-5.25 Linux
Type=Link
URL=http://217.157.2.18/extSupport/webswdb/786%20Drivers/786LCD-5.25%20Linux/
Icon=gnome-fs-bookmark
Name[en_IE]=link to 217.157.2.18 - Drivers 786LCD-5.25 Linux
```

WHY???

Why would anyone want to make things work this way? Excuse my frankness, but in the absence of a REALLY good explanation I am inclined to question the sanity of whoever implemented this. To my mind this behaviour is on par with [Microsoft's LFN/dynamic 8+3 file name generation disaster]("http://navasgrp.home.att.net/tech/clone_copy.htm"). I mean. How broken can you get?

Can this be filed as a bug? Does anyone know how or where? I don't have a clue where to turn with this as I've only been a Linux user for a week. 

Until this is (hopefully!) fixed, I am thinking that doing all your copying at the CLI might be a workaround -- does anyone see any reason why this might not work? 

Also, if I rename (via **mv**) such *.desktop* files at the command prompt, could that cause any problems? I'm guessing that the name displayed on the in the GNOME GUI would stay what it was before even after I rename it via **mv** -- unless I also edit the **Name=** and **Name[en_IE]=** fields?

Finally, what's up with those two fields and them containing my language preference? (**en_IE** <-- That's IE as in Ireland/Eire, not Internet Exploder.) What would happen if those two fields were different? I don't understand half of this (though I fear that once this is explained to me, it may not make a whole lot of sense...).

Can anyone shed any light on this?

---

### Post by ropers on 2006-09-25
I also want to add to my first post in this thread, specifically to my gripe about the unhelpful error message (see image above):

For full functionality, this is what I expect/would love to see in a state of the art GUI:

- When a conflict arises that a file can't be copied, explain precisely why.
- Give the full file name and path. Allow that path/file name to be copied and pasted. 
- If this happens during a multiple file copy/move operation, open up a norton/volkov/midnight commander*-ish* left hand and right hand side window where files that have been copied, files that can't be copied, and files that have yet to be attempted to be copied are all clearly listed, respectively. 

At this point:
- Give the user to option of reverting the entire operation to what things were before the multi-file copy/move operation was started. Yes, that would include restoring overwritten files (meaning they have to be backed up before overwriting -- with the backups only to be deleted once the entire multi-part copy/move operation has completed).
- Give the user the option to cancel and leave all files at what they are now (i.e. some successfully copied, some not). 
- Give the user the option to try copying any further files in the pipeline and then present a list of only those files that failed to copy. 
- Allow the user to save this list as a "file transfer task". 
- Allow the user to reattempt copying/moving the remaining files after resolving whatever condition may have prevented this on the first attempt. Allow this by letting the user double-click on the "file transfer task" that they saved.

Ok, this is a long whish list, and it is WAY presumptious coming from a whining non-programmer who only has ideas to offer. That said, if some actual coders out there like these ideas, then I see no reason why Linux shouldn't provide the best support for copying/moving of multiple files -- as opposed to the above, which in my mind comes close to the worst.

---

### Post by David Marrs on 2006-09-25
> **ropers said:**
> Can this be filed as a bug? Does anyone know how or where?
It wouldn't do any harm. I don't see the benefit in it either, going by your description. Just don't say in the bug report that you think whoever implemented it is insane; he might feel less inclined to see things from your point of view. :p

You could either report the bug directly to the gnome team via bugzilla.gnome.org or to the ubuntu team at launchpad.net. Working out which particular app to file the bug report under might be tricky, but otherwise the process is fairly self-explanatory.

---

### Post by CatKiller on 2006-09-25
> **ropers said:**
> 
WHY???

Why would anyone want to make things work this way?

It's a Gnome thing. All of the launchers on your desktop, panel and in the menus are .desktop files.

> Excuse my frankness, but in the absence of a REALLY good explanation I am inclined to question the sanity of whoever implemented this.

I can't give you that explanation, not being a Gnome developer, but I'd imagine that it gives you a well-defined launcher configuration that works with all locales, allows icons to be changed with Gnome themes, and includes without any trouble a description of what the launcher actually does. There are similar concepts with other desktop environments - having never used KDE or Macs, I can't say what those are - and this is much more flexible than Windows' .lnk files. If you don't like them, you could switch to a different desktop environment, or look through Gnomes specification for .desktop files to see where the flaw is and file it as a bug report.

> To my mind this behaviour is on par with [Microsoft's LFN/dynamic 8+3 file name generation disaster]("http://navasgrp.home.att.net/tech/clone_copy.htm"). I mean. How broken can you get?

Can this be filed as a bug? Does anyone know how or where? I don't have a clue where to turn with this as I've only been a Linux user for a week. 

Until this is (hopefully!) fixed, I am thinking that doing all your copying at the CLI might be a workaround -- does anyone see any reason why this might not work? 

No, it's fine. I've done the same myself when making and editing my own .desktop files - when you make a panel item, it gets a name like bar-0026fb09d2.desktop, which isn't that descriptive. So if I copy it to the Desktop for editing, I'll give it a new name.

> Also, if I rename (via **mv**) such *.desktop* files at the command prompt, could that cause any problems? I'm guessing that the name displayed on the in the GNOME GUI would stay what it was before even after I rename it via **mv** -- unless I also edit the **Name=** and **Name[en_IE]=** fields?

Maybe. I don't really know what's causing your copy problems. Perhaps giving the actual file a different name will fix it, and then you won't get any error message at all.

Edit: actually, I've just read this bit again, and Nautilus will still display the contents of the Name[en_IE] field, regardless of what the file's actually called.

> Finally, what's up with those two fields and them containing my language preference? (**en_IE** <-- That's IE as in Ireland/Eire, not Internet Exploder.) What would happen if those two fields were different? I don't understand half of this (though I fear that once this is explained to me, it may not make a whole lot of sense...).

Can anyone shed any light on this?

That's a feature, not a bug. If they were different, the name for your locale would be displayed. If your locale isn't in the list, the default will be displayed. It may hepl to think of your locale not being something pedestrian like [en_IE], but something like [fa]. Actually, I don't know where that is, but "browser" gets translated as&#1605;&#1585;&#1608;&#1585;&#1711;&#1585; &#1575;&#1740;&#1606;&#1578;&#1585;&#1606;&#1578;&#1740;. You don't have the headache of trying to translate actual filenames, or find the appropriate one for the locale that's being used, even if the locale has changed since the application was installed, and you don't have to leave people who don't use English out in the cold. With minimal hassle, you get one set of files to install, and everyone gets to see information in their own language.

---

### Post by CatKiller on 2006-09-25
If the **actual** filenames contain \, then that may well be your problem. That's used as an 'escape' character, to tell the shell not to interpret whatever comes after it, at least from my limited experience. You might well be able to use the command line to rename the files, and use Tab-completion to hopefully put in the right number of actual escape characters to escape the pretend escape characters that are actually part of the filename.

The bug report should probably be filed with the Firefox people, for making a file with \ as part of the filename. It's not like that would work on Windows, either.

Oh, and the one other instance of this that I came across on an incredibly brief googling was also on copying to a FAT32 filesystem. So possibly that's where the problem of having \ in the filename actually lies.

---

### Post by ropers on 2006-09-25
David, CatKiller: Thanks for your replies! :)


> **CatKiller]
[quote=ropers]Also, if I rename (via mv) such .desktop files at the command prompt, could that cause any problems? I'm guessing that the name displayed on the in the GNOME GUI would stay what it was before even after I rename it via mv -- unless I also edit the Name= and Name[en_IE]= fields?[/quote]

Maybe. I don't really know what's causing your copy problems. Perhaps giving the actual file a different name will fix it, and then you won't get any error message at all.
[/quote]

Removing all characters that are illegal in FAT32 from the actual filename (as seen in the shell) does indeed fix the problem with copying.

[quote=CatKiller]Edit: actually, I've just read this bit again, and Nautilus will still display the contents of the Name[en_IE] field, regardless of what the file's actually called.[/quote]

Yes, I can confirm this as well -- I can rename the file to "something completely different" with **mv** and Nautilus will still show the name for my locale, and in the absence of that it will show the default name. Other than editing the file, there does not seem to be a way to make Nautilus show the real filename.

[quote=CatKiller]If the actual filenames contain \, then that may well be your problem. That's used as an 'escape' character, to tell the shell not to interpret whatever comes after it, at least from my limited experience.[/quote] 
That's correct. I know from my OpenBSD/OS X exposure that you either quote special characters or you escape them. Ie. use either:

[INDENT]"my fancy ph\len4m3"[/INDENT] 

or 

[INDENT]my\ fancy\ ph\\len4m3[/INDENT]

[quote=CatKiller]You might well be able to use the command line to rename the files, and use Tab-completion to hopefully put in the right number of actual escape characters to escape the pretend escape characters that are actually part of the filename.[/quote]

Yes. This actually works quite reliably. 

[quote=CatKiller]The bug report should probably be filed with the Firefox people, for making a file with \ as part of the filename. It's not like that would work on Windows, either.[/quote]

Here I disagree. 
With the ext2 or ext3 (which are "native" to Linux), all bytes except NUL and '/' are legal characters. So there's no reason why a Linux application should not be allowed to use '\', even if this --because of it also being the escape character-- can lead to unruly looking "double-escape" sequences such as in my above example.
The FAT32 file system however has more illegal characters, among them / [ ]  said:**
> Oh, and the one other instance of this that I came across on an incredibly brief googling was also on copying to a FAT32 filesystem. So possibly that's where the problem of having \ in the filename actually lies.


So we've actually got THREE different problems here (which just happened to interact in a strange and initially incomprehensible way in my case):

1. Nautilus' multiple copy/move code is neither smart nor end user friendly. If a copy/move operation fails, the user is never offered a smart suggestion such as "*This file name contains characters not allowed by the destination file system. Would you like to rename it?/Would you like me to rename it automatically?*" Worse, the user can easily find themselves unable to even find out which file was the problem. 

2. GNOME's/Nautilus' *.desktop* file implementation is inconsistent. The fact that with *.desktop* files it displays something else than the actual filename to the user is bad insofar as that it results in some but not all file names getting displayed in Nautilus just the way they are stored on the disk. Is Nautilus a shortcut/application launcher or a file manager? Worse, the .desktop file actually uses --yeuch!-- a file extension! [NEVER, NEVER EVER should you store metadata in the filename.]("http://arstechnica.com/reviews/os/metadata.ars") To do so is imitating a DOS/Windows bug that even MS is slowly moving away from. Why? Why go there?

3. Nautilus' .desktop file implementation does not allow the user to manipulate the actual filename. It's one thing to display an alias that's stored inside the .desktop file in Nautilus instead of the filename. It' quite another thing not to allow the user to even view or change the true filename in Nautilus.


The sub-par handling of errors during multiple file copy/move operations is one issue I've already given you my two eurocents about.

As for the other issues, I see two ways to fix this:

I. Henceforth, have Nautilus display the real **filename** of .desktop files in its  actual file system browser windows. Sure, as part of launchers, sidebars and whatnots, the relevant alias from inside the .desktop file can be used, but as soon as the user is actually browsing the file system --that includes the Desktop-- show the real filename. This would be the solution I'd personally prefer. It's also what Windows does. (Okay, that last point is a really weak one.)

II. 
If the .desktop alias naming stuff is too entrenched now to change it (always a weak argument but anyway), then at least allow the user to edit/rename the real filename in Nautilus. Or make it a user preference whether they want to see the alias/locale name or the real file name. 

Oh, and whatever you do: Get rid of the .desktop naming convention. Don't identify these files by their extensions. Put that metadata elsewhere, even inside the file or whereever.

All that said, if Firefox where to choose to not use special characters when generating .desktop files, for the sake of cross-platform compatibility, well that might be a good thing as well. Though I'm not sure Firefox is responsible for generating these files. (Ie. does Firefox do that or is that already GNOME/OS/Linux code that's doing that? I dunno.)

Thanks and regards,
--ropers

PS: CatKiller, your name freaks me out by the way. I LOVE cats. You're not a dog lover or something?? Or do you mean "cat" as in "person"?

---

### Post by CatKiller on 2006-09-25
> **ropers said:**
> 
Here I disagree. 
With the ext2 or ext3 (which are "native" to Linux), all bytes except NUL and '/' are legal characters. So there's no reason why a Linux application should not be allowed to use '\', even if this --because of it also being the escape character-- can lead to unruly looking "double-escape" sequences such as in my above example.
The FAT32 file system however has more illegal characters, among them / [ ] ; = " \ : | , and *.

You're right. I realised about the FAT limitation after I'd written based on the escape character.

> 2. GNOME's/Nautilus' *.desktop* file implementation is inconsistent. The fact that with *.desktop* files it displays something else than the actual filename to the user is bad insofar as that it results in some but not all file names getting displayed in Nautilus just the way they are stored on the disk. Is Nautilus a shortcut/application launcher or a file manager? 

I think you're actually arguing for *more* inconsistency. Nautilus manages the icons on the desktop as well as icons in a file manager window. Desktop items should be displayed per the .desktop rules. From the name, that would seem to be rather the point. But browsing the files on your desktop in a "proper" file manager window, the file names would be handled differently?

Personally, I agree with you in that there should be some way of finding out what the actual filename is - either in a file manager window, or in the file properties window. It's quite a pain tying the view in a window to the output of **ls** to find the file that you want to edit. But this is a usability argument rather than a consistency one.

> Worse, the .desktop file actually uses --yeuch!-- a file extension! [NEVER, NEVER EVER should you store metadata in the filename.]("http://arstechnica.com/reviews/os/metadata.ars") To do so is imitating a DOS/Windows bug that even MS is slowly moving away from. Why? Why go there?

It seems reasonably likely to me that .desktop files don't have to have a .desktop extension - it's just that way as a convenience. It seems that any text file that starts with [Desktop Entry] could be interpreted as a .desktop file.
> 3. Nautilus' .desktop file implementation does not allow the user to manipulate the actual filename. It's one thing to display an alias that's stored inside the .desktop file in Nautilus instead of the filename. It' quite another thing not to allow the user to even view or change the true filename in Nautilus.

I agree with this, as I indicated above. Mention it to the Nautilus dev team - they won't know what their users would like if we don't tell them.

> The sub-par handling of errors during multiple file copy/move operations is one issue I've already given you my two eurocents about.

I've come across this one myself. Copying symlinks to a FAT partition - an act I've since discovered is not possible due to limitations of the format - led to an "Operation not permitted" error, which led me down a permissions dead-end. Documentation is one area where every project could do with some help.

> I. Henceforth, have Nautilus display the real **filename** of .desktop files in its  actual file system browser windows. Sure, as part of launchers, sidebars and whatnots, the relevant alias from inside the .desktop file can be used, but as soon as the user is actually browsing the file system --that includes the Desktop-- show the real filename. This would be the solution I'd personally prefer. It's also what Windows does. (Okay, that last point is a really weak one.)

I think that this rather defeats the point. If your applications all display Kanji or whatever, and your keyboard inputs Kanji or whatever, why would you want English all over your desktop?

> If the .desktop alias naming stuff is too entrenched now to change it (always a weak argument but anyway), then at least allow the user to edit/rename the real filename in Nautilus. Or make it a user preference whether they want to see the alias/locale name or the real file name.

It's a feature.

But yes, configurability is good. It's probably reasonably straightforward to add a script to the right-click menu to show the filename. Beyond my abilities, though.

> PS: CatKiller, your name freaks me out by the way. I LOVE cats. You're not a dog lover or something?? Or do you mean "cat" as in "person"?

I love cats too - have two of them myself. Cat Killer is an anagram of my surname. Oh and yes, I do like dogs too.

---

### Post by mssever on 2006-09-25
When it comes to handling file types, Gnome just goes about this the wrong way, IMO. Apparently, Gnome decides a file's type by analyzing the first several bytes of the file and comparing that to a mime type database. The problem with this is that it's very difficult to reliably determine a file's type by analyzing its contents. Take PHP files for example. Some (not all) PHP files look nearly identical to HTML, and so Nautilus ignores the php extention and opens them in Firefox. Firefox, of course, can't display the file properly, because Firefos isn't a PHP interpreter.

A Mac-like no-extension method might be fine if Linux supported such metadata, but it doesn't. So, I think that the best way would be to rely on file extensions and fall back to a mime database in the absence of a recognized extension.

And, by the way, the site about metadata that ropers linked to is a bit mistaken when it says that you can't change a file's type without changing the data (another reason to use extensions or something that serves the same purpose). For example, I can take a Windows bitmap file (*.bmp) and change the extension to ico; when I do that, I have a valid Windows icon. In other words, I've just changed the type by simply changing the extension. Also, in Linux when I make a backup of a particular file prior to messing with it in a potentially-destructive way, I typically use a .bak extension. This effective changes the file's type to a backup (I could use another naming convention if I wanted, but the effect would be the same).

---

### Post by ropers on 2006-09-27
CatKiller: stay tuned, I'll respond to you as well.

> **mssever said:**
> When it comes to handling file types, Gnome just goes about this the wrong way, IMO. Apparently, Gnome decides a file's type by analyzing the first several bytes of the file and comparing that to a mime type database.

Which is interpreting the data to glean implicit metadata from it. This is not as good as maintaining proper metadata in the file system, but still better than file extensions.

> **mssever]The problem with this is that it's very difficult to reliably determine a file's type by analyzing its contents. [/quote]

Yes and no. You have a point, but not enough of a point to make file extensions be the better option.

[QUOTE=mssever]Take PHP files for example. Some (not all) PHP files look nearly identical to HTML, and so Nautilus ignores the php extention and opens them in Firefox. Firefox, of course, can't display the file properly, because Firefos isn't a PHP interpreter.[/quote]

I would agree that as bad as file extensions are, as long as they are still the dominant method of file type/creator identification in the real world, they should not be ignored if present. Regarding your PHP example you could still fairly reliably determine the file type from the file's content by looking at the whole content: Does it contain a single PHP tag? If yes, then it's a PHP file. Yes, there are PHP files which do not currently contain PHP tags (but may when updated, which is why they are PHP files), but even if the system "erred" on that one and "incorrectly" inferred that the file was an XHTML file, it wouldn't matter as Firefox can display XHTML.

[QUOTE=mssever]A Mac-like no-extension method might be fine if Linux supported such metadata, but it doesn't.[/quote]

Actually, as the article also mentions, the Mac has gone back in time: It did have a fairly ok metadata system. Not a perfect system, mind you, but a good system nontheless. But it's moved away from that to file extensions, which is really rubbish. I can admittedly see a possible reason for that, maybe they want to be Windows-compatible at all costs and after going back to file extensions are planning to adopt whatever metadata system MS is going to adopt. That's maybe a non-irrational strategy, but it also makes Apple the hanger-on, not the innovator. I'm not fully convinced. And I really think file extensions are a moronic system. Conflating type/creator metadata and a file's name is a really dumb idea and generally speaking not something Ubuntu/GNOME should emulate. MS themselves are definitely moving to metadata. E.g. google for Alternate Data Streams Windows (though most posts tend to focus on the commonly overlooked vulnerabilities MS has --surprise-- introduced with their current implementation).

[QUOTE=mssever]So, I think that the best way would be to rely on file extensions and fall back to a mime database in the absence of a recognized extension.[/quote]

As an interim strategy, maybe (see above). But certainly not as an overall goal.

[QUOTE=mssever]And, by the way, the site about metadata that ropers linked to is a bit mistaken when it says that you can't change a file's type without changing the data (another reason to use extensions or something that serves the same purpose). For example, I can take a Windows bitmap file (*.bmp) and change the extension to ico said:**
> 

The way I understand Siracusa, what he means is that conflating two different kinds of data --file names and (other) metadata in this case-- is a really dumb idea. IMHO it's open to argument but quite irrelevant whether the file name is to be considered part of a file's metadata (I would personally tend to think so) or a file's data. In any case, the way I understand Siracusa, what he is complaining about is that in order to change your bitmap file to an icon file you have to change its name. The name shouldn't ever enter into it. You should be free to choose any name you want with any filetype you want, and yes, you should be allowed to e.g. call a PDF file "very.urgent.doc". The trouble is that this insuffici.ent sys.tem is now so entrenc.hed that it's difficult to innovate your way away from that. Which doesn't however mean one shouldn't try.

[QUOTE=mssever]Also, in Linux when I make a backup of a particular file prior to messing with it in a potentially-destructive way, I typically use a .bak extension. This effective changes the file's type to a backup (I could use another naming convention if I wanted, but the effect would be the same).

This is a different case. You see, to create a backup file in the same folder, you're only supposed to change its name -- you're not supposed to change the file type/creator metadata: this should stay the same with the backup file. In the case of using file extensions as substitute for file/creator metadata, it only SEEMS like you've changed the file type/creator info the moment you changed the file name to something.bak. (After all, the extension is the poor man's file/creator metadata under that system.) However you could argue that that's not the case, you've only changed the name. If you used a fully working metadata system with proper file type/creator metadata, you could still name your backup files something.bak and doing so would be entirely correct and not at odds with your metadata implementation and convention at all. But this is becoming a largely philosophical argument and is splitting hairs now, so I'll not further argue this particular (less important) special case.

---

### Post by mssever on 2006-09-27
> **ropers said:**
> I would agree that as bad as file extensions are, as long as they are still the dominant method of file type/creator identification in the real world, they should not be ignored if present. Regarding your PHP example you could still fairly reliably determine the file type from the file's content by looking at the whole content: Does it contain a single PHP tag? If yes, then it's a PHP file. Yes, there are PHP files which do not currently contain PHP tags (but may when updated, which is why they are PHP files), but even if the system "erred" on that one and "incorrectly" inferred that the file was an XHTML file, it wouldn't matter as Firefox can display XHTML.
Analyzing the entire file just to determine its type would be resource-intensive--particularly if the file was large. And even then, it would be diffucult to be 100% accurate in determining the type. For example, one form of the PHP opening tag is <? which is also used by XML. This problem could be easily solved by a metadata system like the older Macs used. By the way, I used System 7.1 for many years, so I have a fairly good grasp of the old Mac way of doing things (I've barely used MacOS X, though).

Incidentilly, the UNIX concept of extensions is a little different. Back before GUIs became dominant, *nix users used extensions as a human-readable reminder of the file type (and MS copied this in DOS and codified it into law). This was due to a large degree to the fact that you had to tell the system what program to use to open a particular file. But extensions never became entrenched in the UNIX/Linux world as they are in Windows. In fact, executable files (and many non-executable system files, as well) generally have no extension, unless the creator uses one to remind him/her what type of executable it is. Instead, non-binary executable files contain a shebang line that tells the system what program should be used to open it. And executable files themselves are identified by filesystem metadata.

EDIT: Just noticed in your signature that you have OpenBSD experience, so you probably know this already.

> The way I understand Siracusa, what he means is that conflating two different kinds of data --file names and (other) metadata in this case-- is a really dumb idea. IMHO it's open to argument but quite irrelevant whether the file name is to be considered part of a file's metadata (I would personally tend to think so) or a file's data. In any case, the way I understand Siracusa, what he is complaining about is that in order to change your bitmap file to an icon file you have to change its name. The name shouldn't ever enter into it. You should be free to choose any name you want with any filetype you want, and yes, you should be allowed to e.g. call a PDF file "very.urgent.doc". The trouble is that this insuffici.ent sys.tem is now so entrenc.hed that it's difficult to innovate your way away from that. Which doesn't however mean one shouldn't try.I suppose that this is somewhat a philosophical issue. To change a file's type in the Windows world, I rename it. Easy, but not necessarily logical. In the old Mac world, I fire up ResEdit, let it create a resource fork, and change the type and/or creator. More logical, but definitely more complicated.

So, in the end, I can be happy with either a Windows-like system which works perfectly 100% of the time even if it isn't the most philosophically correct way, or an old Mac-like system which also works perfectly but isn't quite so easy to implement in an existing system. But the Gnome system of mime-type guessing is terrible broken, IMHO.

---

### Post by ropers on 2006-09-28
> **mssever said:**
> Back before GUIs became dominant, *nix users used extensions as a human-readable reminder of the file type (and MS copied this in DOS and codified it into law).

(...)

EDIT: Just noticed in your signature that you have OpenBSD experience, so you probably know this already.

This bit of historical background info I did not know. It seems to me that this is an example of instruction creep:
1. Unix informally estalishes file extension purely as user-friendly naming conventions.
2. DOS copies file extensions and institutes them as a file type/creator metadata substitute.
3. There is no step three.

Very interesting to know.

EDIT: Yes there is a third step: 3. UNIXarian OSes start adopting this bad DOS/Windows practice. Everybody suffers.

[QUOTE=mssever]I suppose that this is somewhat a philosophical issue. To change a file's type in the Windows world, I rename it. Easy, but not necessarily logical. In the old Mac world, I fire up ResEdit, let it create a resource fork, and change the type and/or creator. More logical, but definitely more complicated.

So, in the end, I can be happy with either a Windows-like system which works perfectly 100% of the time[/quote] 

s/100% of the time/most of the time/g

[quote=mssever]even if it isn't the most philosophically correct way, or an old Mac-like system which also works perfectly but isn't quite so easy to implement in an existing system. But the Gnome system of mime-type guessing is terrible broken, IMHO.[/QUOTE]

Yes -- based on what I know now (did I mention I'm a Linux/GNOME n00b?), I would agree that it's got problems. I'd much prefer to live in an ideal work though, where we would have one perfect and extensible metadata system in use across all platforms and file systems.

Also, I'd love to have a cat. ;-)

---

### Post by ropers on 2006-09-30
> **CatKiller said:**
> I think you're actually arguing for *more* inconsistency. Nautilus manages the icons on the desktop as well as icons in a file manager window. Desktop items should be displayed per the .desktop rules. From the name, that would seem to be rather the point. But browsing the files on your desktop in a "proper" file manager window, the file names would be handled differently?

No, I didn't say that. I wrote:[quote=ropers]Sure, as part of launchers, sidebars and whatnots, the relevant alias from inside the .desktop file can be used, but as soon as the user is actually browsing the file system --that includes the Desktop-- show the real filename. This would be the solution I'd personally prefer.[/quote] AFAIK Nautilus is "responsible" both for displaying what's on the Desktop and what can be seen in its file system browser windows. The Desktop is a directory in the file system and Nautilus doesn't treat it any different, whether you're viewing your Desktop folder via the Nautilus file system browser, or whether you're looking right at it. What I meant was: Show the real filename in the file system browser and on the actual Desktop, but feel free to show some other name you set in, say the Applications launcher menu if you wish. Be consistent, let the file system be the file system without any confusion, but if you want alternate titles to display in launchers or whatnot, then hey! that's ok! 

[quote=CatKiller]
Personally, I agree with you in that there should be some way of finding out what the actual filename is - either in a file manager window, or in the file properties window. It's quite a pain tying the view in a window to the output of **ls** to find the file that you want to edit. But this is a usability argument rather than a consistency one.[/quote]

Nolo contendere. :)

[quote=CatKiller]
It seems reasonably likely to me that .desktop files don't have to have a .desktop extension - it's just that way as a convenience. It seems that any text file that starts with [Desktop Entry] could be interpreted as a .desktop file.[/quote]

Ah. I just tested this and you're right. I cede that point. :)

[quote=CatKiller]
[quote=ropers]
3. Nautilus' .desktop file implementation does not allow the user to manipulate the actual filename. It's one thing to display an alias that's stored inside the .desktop file in Nautilus instead of the filename. It' quite another thing not to allow the user to even view or change the true filename in Nautilus.
[/quote]
I agree with this, as I indicated above. Mention it to the Nautilus dev team - they won't know what their users would like if we don't tell them.
[/quote]
In your opinion, what would be the best/nicest/easiest way of submitting such feedback to the GNOME guys? [http://bugzilla.gnome.org](http://bugzilla.gnome.org) ? [http://mail.gnome.org/mailman/listinfo/gnome-list](http://mail.gnome.org/mailman/listinfo/gnome-list) ? 
Have you ever been in touch with them? 

[quote=CatKiller]
[quote=ropers]I. Henceforth, have Nautilus display the real filename of .desktop files in its actual file system browser windows. Sure, as part of launchers, sidebars and whatnots, the relevant alias from inside the .desktop file can be used, but as soon as the user is actually browsing the file system --that includes the Desktop-- show the real filename. This would be the solution I'd personally prefer. It's also what Windows does. (Okay, that last point is a really weak one.)[/quote]
I think that this rather defeats the point. If your applications all display Kanji or whatever, and your keyboard inputs Kanji or whatever, why would you want English all over your desktop?[/quote]

I don't. And I don't see why the *actual filename* couldn't be in (unicode-)Kanji. IIRC, in Windows and Mac OS X, if you drag a bookmark to the dektop, it saves it as a file named after the web page title, to the extent that the file system nameing conventions will allow it. Yes, that includes Kanji filenames. I will admit that Kanji filenames would be a challenge without an input system, but in OS X for example I occasionally did switch to Japanese input to type in hiragana or katakana. This is even less of a challenge if using tab-completion on the command line. IMHO we should move away from considering English the default and "easier to handle". Millions of Chinese would disagree. I'd much rather have Japanese/Chinese/whatever filenames where appropriate (e.g. for Japanese/Chinese/whatever bookmarks) than artificially introduce a difference between the file name and the name displayed on the desktop. Again, to the extent that the Desktop is just another folder in the file system, I'd much rather have ALL files in it behave like any other files. 

And if we really MUST have files such as .desktop files that behave differently, then at least there should be a way to handle the actual filenames, and there preferably should be a way to **disable** that "feature", so those of us who prefer consistency over the supposed comfort of having strings from inside of these .desktop files displayed on the Desktop in lieu of the filename can have a way to enable that. Actually, I think we kind of agree here -- you already wrote that you'd also like to see configurability.

:)

Thanks and kind regards,
--ropers

---

### Post by CatKiller on 2006-09-30
> **ropers said:**
> In your opinion, what would be the best/nicest/easiest way of submitting such feedback to the GNOME guys? [http://bugzilla.gnome.org](http://bugzilla.gnome.org) ? [http://mail.gnome.org/mailman/listinfo/gnome-list](http://mail.gnome.org/mailman/listinfo/gnome-list) ? 
Have you ever been in touch with them?

I haven't, I'm afraid.

I happened to be looking at something else, and noticed that this whole .desktop thing isn't a GNOME thing, it's a [freedesktop.org spec]("http://www.freedesktop.org/wiki/Standards_2fdesktop_2dentry_2dspec"). I think. I don't know what the KDE implementation is like - Ubuntu is the only Linux distribution I've used.

> I don't. And I don't see why the *actual filename* couldn't be in (unicode-)Kanji. IIRC, in Windows and Mac OS X, if you drag a bookmark to the dektop, it saves it as a file named after the web page title, to the extent that the file system nameing conventions will allow it. Yes, that includes Kanji filenames. I will admit that Kanji filenames would be a challenge without an input system, but in OS X for example I occasionally did switch to Japanese input to type in hiragana or katakana. This is even less of a challenge if using tab-completion on the command line. IMHO we should move away from considering English the default and "easier to handle". Millions of Chinese would disagree. I'd much rather have Japanese/Chinese/whatever filenames where appropriate (e.g. for Japanese/Chinese/whatever bookmarks) than artificially introduce a difference between the file name and the name displayed on the desktop. Again, to the extent that the Desktop is just another folder in the file system, I'd much rather have ALL files in it behave like any other files.

This won't work. Yes, all user-created files can be named whatever the user can get into the filename. But without a disconnect between what the file is called and what is displayed on the user's computer we have one of two possibilities:

1) Every application must be localised file-by-file for every version. This will almost certainly break after the first update, and mean that data will not be portable between locales.

2) All files will be named and displayed according to the language of the developers of the application. This will probably be English for most applications. Given that it is one of the stated aims of the Ubuntu project "that software tools should be usable by people in their local language and despite any disabilities", this is not acceptable.

> And if we really MUST have files such as .desktop files that behave differently, then at least there should be a way to handle the actual filenames, and there preferably should be a way to **disable** that "feature", so those of us who prefer consistency over the supposed comfort of having strings from inside of these .desktop files displayed on the Desktop in lieu of the filename can have a way to enable that. Actually, I think we kind of agree here -- you already wrote that you'd also like to see configurability.

Yes, this is the only flaw that I find in the GNOME implementation from our discussion. I think we'll have to agree to disagree about the filenames :) So what we both definitely want is the ability to view and manipulate the filename through Nautilus. This has already (sort of) been files as a bug in [GNOME's  bugzilla]("http://bugzilla.gnome.org/show_bug.cgi?id=107417"). Perhaps one of us ought to elaborate on it?

---

