---
title: "Problem with greek characters (installation, ntfs files, openoffice, typing)"
date: 2004-12-06
forum: Desktop Environments
---

### Post by orestis82 on 2004-12-06
Hello there.

I've tried Ubuntu and it is pretty nice. However I have major problems with Greek characters.

I chose Greek during the installation, and I was amazed to find that most of the installation was in Greek.

However, during the second part, where Ubuntu boots from the hard disk to configure the packages, some questions did not display correctly. I could see all english characters, but the dialogs were mostly blank boxes. It seems that the default values were good, because I couldn't see what I was doing.

Anyway, I proceed to my brand new Ubuntu desktop. The fonts look good, although strangely the pi character (&#960;) is bold and italic. I don't know if this a problem with font anti-aliasing.

I log-in, launch OpenOffice and try to enter Greek characters. Alt-shift (default windows shortcut) doesn't work, so I install the keyboard indicator desklet. I see that Greek is already present. Hooray.

But when I try to type greek text in OpenOffice, despair. The default font is plain ugly, italic and has very big spaces between the letters. I try some other fonts to the same effect. I find FreeSerif and it works. However, accented greek letters (&#940;,&#941;,&#943;,&#942;,&#973;,&#972;,&#902;,&#904;,&#906;,&#905;,&#910;,&#908;,&#970;,&#971;,&#912;,&#944; ) don't work. Greek keyboards type those letters by pressing ";" and then the normal letter. The key ";" is indeed dead, but I can see no accents.

I then go to search my partitions, I find that my windows partitions weren't mounted. I hunt around with fstab and mount and I manage to mount my FAT32 partition, but the NTFS partitions gave some error about permissions when I try to access them. They mount correctly though.

When I browse my FAT32 harddisk, I find that all my greek filenames are now ???????. I can browse them, and edit files, but the filenames (and folder names) are all question marks.

Please help me resolve these problems.

Running Warty, fresh install from CD, no updates (since I can't get my USB modem to work)

---

### Post by orestis82 on 2004-12-07
Hey, I have managed to solve most of those issues:

Issue 1: It seems that ubuntu is not choosing a correct greek-capable font when displaying the initial login screen. So it is using font-switching to display the greek characters. However the greek leter pi is present in most fonts, so it is displayed from the default font. Maybe make all menus to be displayed in a UTF8 font to avoid this ?

Issue 2.1: I installed the fonts from Windows. I had some trouble with permissions, but I fixed those, and now most greek fonts look good.

Issue 2.2: However, I still can't add accented letters in OpenOffice. I can do it everywhere else, and I can paste accented letters in OpenOffice, so I think this is OpenOffice related. I hunted in the Options but didn't find anything to fix this.

Issue 3: Just added utf8 to my partition:
/dev/hda1       /media/data     vfat utf8,defaults,auto,uid=1000,gid=1000 0       0

and everything looks good. I can't see greek filenames in gnome-terminal. I tried putting codepage=737 (the greek codepage) but still no luck.

Issue 4: I plugged the modem in the serial port (it has both USB and serial), and I configured CHAP authentication (my ISP wants CHAP, not PAP). Disabled lcp-echo-interval and lcp-echo-failure because my connection was failing due to some ping requests, and it's working!!! I'm posting now from my Ubuntu 
Desktop.

---

### Post by wayover13 on 2004-12-07
I have some experience with inputting Greek in Open Office, though it's mostly been under Debian.  I've used the Gnome desktop keyboard switching tool to do this in Ubuntu, but haven't experimented with it much so far.  Anyway, it sounds like your problem is with keyboard mapping: the characters are there in your font set, but the keyboard is not mapping them--including the so-called dead keys you typically use for the diacritical marks.  From what you're saying and the bit of experimentation I've just now done, I'd say the Gnome keyboard switching tool is defaulting to some specific font--which shows that the tool is still a bit immature.  I've selected polytonic Greek as an alternate in the Gnome keyboard switching dialogue--that's the one that's supposed to get you the diacriticals.  I'll have to look into this some more, but I'll at least post here a link to a discussion I had (pretty much with myself) on getting Cyrillic and Greek polytonic input working in OpenOffice.org Writer (under Debian).  Here's the link:
[http://www.oooforum.org/forum/viewtopic.php?t=12780&sid=7ad45dcd12cc07461328efd39695dfa0](http://www.oooforum.org/forum/viewtopic.php?t=12780&sid=7ad45dcd12cc07461328efd39695dfa0)
.  It's not Ubuntu-specific at all, but contains related information as well as some links to other sites where you might find help.

James

PS  I manually edited XF86Config-4 in Debian to get the keyboard switching and font functionality I wanted.  I remember there was a slight problem with one or more of the diacriticals, but I did get most of the functionality I wanted using that method.  I was definitely able to switch fonts--to Times or whatever font supported unicode characters in the desired range.

---

### Post by orestis82 on 2004-12-08
Greek polytonic isn't what I want. Greek polytonic is not used any more, the only purpose to use greek polytonic is linguistics and ancient greek studying.

Greek polytonic has many accents (5, plus some special "symbols" that go under the letter for some letters).

Greek modern (what we use now) uses only one accent. I can type modern Greek in all other applications. I can also use the special insertion tool (applet) to paste greek polytonic in OpenOffice. I just can't type them. In the Windows version everything is working good.

Maybe I should browse the OpenOffice bugzilla and post a bug there.

---

### Post by wayover13 on 2004-12-08
I wasn't saying that you need Greek polytonic.  I was discussing my experience inputting Greek in OOo and mentioned polytonic because it's similar: it also uses dead keys for producing accent marks.  Isn't that obvious?  It's the closest thing you've gotten to a relevant response so far--and that you're likely to get in this forum.  We call this "related generic discussion" in English.  I now have input for all polytonic diacriticals (linked to dead keys ' and ] and ; for example) in OOo working and am able to choose different fonts, btw.  Happy bug filing over at OpenOffice.org.

James

---

### Post by orestis82 on 2004-12-08
Hey, take it easy.

I thought that you described that I need Greek polytonic, and I was just making myself clear. Sorry if it came out harsh - I'm not a native speaker.

---

### Post by wayover13 on 2004-12-08
Ok.  If you need any further info from me about how I got polytonic input--with dead key functionality and font switching ability--working in OOo, just let me know.  Might be quite similar to what you'd need to do for modern Greek accent inputting.

James

---

### Post by orestis82 on 2004-12-08
It would be great if you described it step-by-step.

Thank you.

---

### Post by wayover13 on 2004-12-08
Ok.  I can describe what I've done.  I can't say for sure which point actually got things working: I tried a number of things I knew of, having faced the problem of Cyrillic/Greek polytonic input in OOo before.  I was focusing on getting a unicode solution working, I can say that.

The first thing I did was try switching to different font faces in OOo, to confirm I had the same problem you described.  True enough, all the ones I tried in Greek gave some wierd, semi-italic looking font with ridiculously large spacing between letters.  I decided that perhaps I did not have unicode enabled on the system.

So, I opend a console and issued < sudo dpkg-reconfigure locales >.  This is a Debian solution using the CLI--not sure if Ubuntu/Gnome give some gui equivalent.  This gives you a menu of localizations you can put on the system.  As I understand it, this helps the system to display other codemaps or understand unicode font assignments for these other languages.  I chose a unicode (English one) for the system's default, but I also ticked Greek and Russian unicode locales there.  You may want to make Greek unicode your system's default: I think it's el_GR.UTF-8.  I'm not sure if this is what resolved the problem, but it is something that I did.

I recall trying font switching in OOo afterward and not seeing much difference.  I rebooted (for other reasons) sometime in here, and decided to copy over some fonts from my other system to try and tackle this further.  I copied over all the Windows fonts I had on that system, as well as some other ancient Greek fonts and a nice unicode font called "Gentium" that I had downloaded.  After loading those fonts, I fired up OOo again and decided to try Gentium first, since I knew it was unicode and since I had used it previously to input Greek.  It worked.  I was able to get all the diacriticals using the dead keys, too.

Since then, I've tried a few different fonts.  Several work fine and give me much better looking Greek characters than that wierd default font.  It seems when I select an incompatible font, it defaults to that wierd looking one we've been talking about.  I was able to get Arial, Courier, Garamond and several others to display nice looking, slightly differing Greek fonts.

My supposition is maybe you need to enable a unicode Greek locale for your system to get this working.  Perhaps your not having unicode enabled on the system causes OOo to default to the only Greek font it can use.  Once you've enabled unicode, download and try out the Gentium font.  I seem to recall you saying your Windows fonts, which display Greek characters (unicode?) under Windows are not working in Ubuntu.  Maybe again because a unicode locale needs to be specified.  This could also be a permissions issue: I had some trouble when I copied over Windows fonts to my system.  Since the permissions didn't get set right, I couldn't use them.  Fonts themselves need to be set 644, and the directories they are in 755.

Hope that helps.  Sorry to be a bit vague, but I'm not totally conversant in these matters and am not absolutely sure what solved the problem for me.  But trying/checking some or all these things might get your Greek input working in OOo.

James

---

### Post by joe.turion64x2 on 2006-11-23
Hi, I am having problems with strange characters in filenames of OpenOffice documents, namely, if I have a file named canción.odt and try to open it by double clicking it, OpenOffice.org displays an error message saying that the file doesn't exist [-( .
Is this related to the problem you are dealing with (Greek)? Can you give me a clue to solve my problem? :confused:
Thanks in advance.

Just for completeness :KS I will say I am running the 32bits version of Ubuntu 6.10 and OpenOffice.org 2.0.4 (the one downloaded from [www.openoffice.org](www.openoffice.org), not the buggy one provided with Ubuntu).

---

