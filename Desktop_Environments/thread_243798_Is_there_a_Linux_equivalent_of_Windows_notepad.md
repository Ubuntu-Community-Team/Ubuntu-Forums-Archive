---
title: "Is there a Linux equivalent of Windows notepad ?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Raptor Ramjet on 2006-08-25
Hello,

I was just wondering if there is a Linux equivalent of the excellent Windows notepad program ?  e.g. A very simple text file editor that will attempt to load *any* file - regardless of content.

I ask as I have just been trying to use gedit to look at an arbitary file (supplied as part of a firmware upgrade for my router) but gedit refuses to open the file as it "might be binary".  Cue me "Yes, thankyou it is indeed binary but I want to view it anyway...".

However I then switch to my Windows box and can happily view the same file in Notepad - which lets me see the text messages in the file which is what I was interested in doing.  It also displays loads of "blobs" and weird symbols where the unprintable ASCII characters are but who cares ?  As long as I don't save the file it's not an issue.

Now I know there are many "fancy" text, not to mention hex, editors and viewers available for *NIX but what I'm after is a completely dumb program that just does what I ask - open a file and present the content in a text box/text area.

If not I suppose I can knock one up in mono but I'm guessing that there's already one *somewhere*.  

When dealing with computers sometimes less really is more.

Cheers.

---

### Post by Metacarpal on 2006-08-25
On Ubuntu/Gnome: gedit
On Kubuntu/KDE: kate

---

### Post by NESFreak on 2006-08-25
in grafical mode: what Metacarpal says

in commandline mode: nano (familiar in use) or vim (hard to understand at first, but faster when you get to know how it works.

---

### Post by aysiu on 2006-08-25
Gedit has some weird bug in it... actually, I think it's Nautilus that's the problem, not Gedit... that stops you from opening certain files it deems dangerous. I think it's ridiculous, and I may have even filed a bug report on it at one point. [Here's a thread I posted last year on the problem](http://ubuntuforums.org/showthread.php?t=48312).

Use Konqueror/Kate if it bothers you that much. Kate can open anything, and both Kate and Gedit are way better than Notepad.

In Windows at work, I use Notepad++ because Notepad and Wordpad are so feature-lacking.

**Edit**: If you really like Nautilus and Gedit, you might want to try editing the preferences in Nautilus to always view files instead of executing them. (See attached screenshot.)

---

### Post by carontis on 2006-08-25
Your question is about a similar program inside the system. In Ubuntu you find the same to the Notepad for windows, in Applications --> Tools --> Text Editor. You should seen it very easily. That's the first simple editor, exactly as it is for windows the notepad, but remember that if you need to export files made with it, you will have to save them and only after add the extension _.txt_ for reading it with windows, or the win platform will answer you is impossible to open it.

---

### Post by NoWhereMan on 2006-08-25
mousepad is the nearest neighbour to windows notepad; it is bundled in xubuntu, but you should be able to find it as a single package, anyway :)

---

### Post by hajk on 2006-08-25
> **Raptor Ramjet said:**
> Hello,

I was just wondering if there is a Linux equivalent of the excellent Windows notepad program ?  e.g. A very simple text file editor that will attempt to load *any* file - regardless of content.


You wouldn't want it to be equivalent to NotePad, I think, since NotePad requires LF/CR line endings, wheras the *nix world uses only LF. Now, if you meant WordPad...:razz:

---

### Post by Raptor Ramjet on 2006-08-25
Now I don't wish to be rude but I did expressly say in my post that gedit *does not* do the job so telling me to try gedit is just annoying :)

However having just tried Kate (after waiting for loads of KDE stuff to install) that works nicely and is "just what the doctor ordered".  So I think that I'll be replacing the gedit shortcut with one for Kate  as it seems to have just the right level of mindlessness that I want in my simple text editor :)

Sometimes you just want to "open the file and go".  No formatting, no syntax highlighting, in fact no "intelligent" interpretation of data at all - just open the damn buffer and display it whether this produces a corrupt garbled display or not.

So cheers for the replies !

---

### Post by ajgreeny on 2006-08-25
I'm sure gedit used to open the files of any type in breezy with the same warning you get in kate if it is a binary file type (telling you it will be corrupt if you save it rather than just close it), but as I now use kubuntu I can't remember what the situation was in ubuntu dapper.  Has the bug mentioned above come with dapper version of gedit or is my memory playing tricks on me  - again?

---

### Post by hajk on 2006-08-25
> **Raptor Ramjet said:**
> 
Sometimes you just want to "open the file and go".  No formatting, no syntax highlighting, in fact no "intelligent" interpretation of data at all - just open the damn buffer and display it whether this produces a corrupt garbled display or not.


I always use "view" just to simply have a look at what's there in a file, opens everything you throw at it, even binary or PDF...

(No need to know that it'll actually be vi in a read-only mode, but people who realize that will use typical vi-paging commands to their advantage...)

---

### Post by OffHand on 2006-08-25
```
sudo apt-get install leafpad
```

---

### Post by ash211 on 2006-08-25
I'm actually a fan of kedit on KDE.  It's even cleaner than kate is.  If kate is wordpad from windows, then kedit would be notepad.

---

### Post by aysiu on 2006-08-25
There's also KWrite, too.

---

### Post by peabody on 2006-08-25
Wow, I didn't know that about gedit.  In fact, now that I know that about gedit I'm kinda pissed off!  It's all well and good to inform the user about something that may seem strange, but my God, not even providing a way to get around it?

Ironically, wine comes with a notepad.exe.  It's not the windows notepad, but it behaves just like it.  It should be in ~/.wine/drive_c after installing and running winecfg.

---

### Post by reclusivemonkey on 2006-08-26
> **Raptor Ramjet said:**
> Now I don't wish to be rude but I did expressly say in my post that gedit *does not* do the job so telling me to try gedit is just annoying :)

LOL I was only reading your post and it annoyed me too dude ;-)

The "Linux" way of looking at a file would be to use the CLI (as always), and the command of choice would be "cat". "tail" and "head" may also be useful to you. The man pages for each of these will tell you more. If you really subscribe to the "less is more", you can also check out the "less" and "more" commands!

---

### Post by aok on 2006-08-26
In a terminal, you can type:

```
strings binaryfile.dat
```

and the output will only be strings of at least 4 printable characters in a row (can be adjusted).

---

### Post by mdurham on 2006-08-26
OffHand, 'leafpad' doesn't seem to work for me. It truncates at what it must beleive is an end of file and only shows a few chars.

---

### Post by kerry_s on 2006-08-26
You can try gtkedit it is a notepad clone, look here and see if it's got what you want-> [http://gtkedit1.sourceforge.net/](http://gtkedit1.sourceforge.net/)

It's in the repos so it's easy to install with apt-get or synaptic.

---

### Post by mdurham on 2006-08-26
gtkedit like leafpad doen't display binary files.
A program like notepad or wordpad would be very useful sometimes.

---

### Post by aysiu on 2006-08-26
> **mdurham said:**
> gtkedit like leafpad doen't display binary files.
A program like notepad or wordpad would be very useful sometimes.
Use Kate. It's been mentioned before in this thread.

---

### Post by lexxonnet on 2006-08-27
> **aysiu said:**
> There's also KWrite, too.

Kate actually depends on and uses Kwrite :) Its pretty much Kwrite with a konsole, and a file list and things of the sort build in

---

### Post by NoWhereMan on 2006-08-27
so you really don't like mousepad? :D

---

### Post by steve.horsley on 2006-08-27
How about ghex2, in package ghex. It's a proper hex editor and as such will allow ediing any file, and won't hide bits from you.

---

### Post by mdurham on 2006-08-27
I'm not sure if you guys are reading this correctly but:
Raptor Ramjet wanted an editor (or viewer) that displayed a files contents regardless of the contents type, i.e. text or binary.
> A very simple text file editor that will attempt to load *any* file - regardless of content.
None of the suggestions like 'leafpad' 'mousepad' etc will do this, so I wonder why you recommend them. Have you actually tried looking at a binary file with them, or are you just guessing that these progs will work as desired?
Cheers, Mike

---

### Post by aysiu on 2006-08-27
Kate does it, but apparently you're ignoring that fact.

---

### Post by mdurham on 2006-08-27
you're quite correct aysiu, kate seems to be the only one capable of doing the job. Thanks.

---

### Post by aysiu on 2006-08-27
Sure. I just tested it, and Gedit can open binary files if you open Gedit first and then open the binary file through the "open" dialogue instead of navigating the binary file first and then trying to open it with Gedit.

Does that make sense?

---

### Post by janhenderson on 2006-08-27
> **Raptor Ramjet said:**
> Now I don't wish to be rude but I did expressly say in my post that gedit *does not* do the job so telling me to try gedit is just annoying :)

However having just tried Kate (after waiting for loads of KDE stuff to install) that works nicely and is "just what the doctor ordered".  So I think that I'll be replacing the gedit shortcut with one for Kate  as it seems to have just the right level of mindlessness that I want in my simple text editor :)

Sometimes you just want to "open the file and go".  No formatting, no syntax highlighting, in fact no "intelligent" interpretation of data at all - just open the damn buffer and display it whether this produces a corrupt garbled display or not.

So cheers for the replies !

I'm a big fan of kate; you can also use kwrite, which is simpler than kate, and you can also use leafpad which is the closest to notepad I'd seen.

---

### Post by mdurham on 2006-08-28
I opend Gedit first as you suggested but it doesn't work for me with binary files. Try it on a ...gz or ...zip
> gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

---

### Post by aysiu on 2006-08-28
Hm. Yeah, I didn't try it on a .gz or a .zip. I tried it on binary files in the /usr/bin directory. Well, we've got Kate...

---

