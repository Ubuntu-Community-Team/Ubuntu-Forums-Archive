---
title: "Change character encoding for PAR2 files"
date: 2009-06-20
forum: General Help
---

### Post by ricardisimo on 2009-06-20
I keep running into the same problem over and over again, where song titles with special characters (accents, tildes, umlauts, etc.) become invisible to the selfsame parity files that were generated to check them after download. There's no way for me to check their integrity, and there are rarely enough PARs to replace entire songs.

I'm assuming that if I can change the character encoding either to or from UTF-8 or ISO-8859-1, or one of the usual suspects... that I can correct this problem. Is this assumption correct, and how do I do it? Thanks in advance.

---

### Post by ricardisimo on 2009-06-21
Does anyone else even know what I'm talking about?

I found one batch of songs with enough PARs to replace the entire one missing song, but it replaced it very strangely. It was something like this:
```
from "01 - Sénégal.mp3" to "01 - S&#65533;n&#65533;gal.mp3 (incorrect encoding)"
```
And it just so happened that the md5sums of the original and the replacement were identical, so it was moot in this case. Still, I'd like to know how I can bypass this.

Is the Replacement Character ("&#65533;") a universal wildcard? Can I just pop it in there? Worth a shot, no? I still say I should be able to alter the encodings within a single folder to get the PARs to read correctly. Anyone?

---

### Post by ricardisimo on 2009-06-21
No, it doesn't work. I tried dropping the "&#65533;" in wherever needed, but nautilus would immediately rename the file, attaching the text " (invalid encoding)" to the tail of the filename.

So the question becomes, once again, how do I change character encodings in a specific folder? Or is there, perhaps, another wildcard character I can use?

---

### Post by ricardisimo on 2009-06-23
I'm assuming no one is responding because so few people use newsgroups anymore, which is not only sad but bizarre, considering the quantity and quality of material that is simply unavailable from any other store or resource.

Oh,... and another thing: bump.

---

### Post by ricardisimo on 2009-06-24
More info, by way of another bump...

GPar2 won't show me the names of the files for which it is searching, and pypar2 will show me, but won't let me copy (so that I could rename the files in question with an exact copy/paste).

Any suggestions?

---

### Post by ricardisimo on 2009-06-24
Further proof that the General Help forum is not the place to post. Better to play the part of noob and post in Absolute Beginners, which is probably my next step.

No one has ever experienced this problem?

---

### Post by ricardisimo on 2009-06-26
In System >> Administration >> Language Support, there is an option that says "Use input method engines (IME) to enter complex characters". Is this in any way related to my issue?

---

### Post by ricardisimo on 2009-06-28
The other option that I can see is System >> Preferences >> Keyboard >> Layouts, and then I can select United States-USA, and maybe that would change the character encoding. The problem is that it would be system-wide, rather than just in the one affected folder, and I really love my current keyboard setup, and I'd rather not have to remember to switch back and forth.

Any recommendations?

The obvious solution - at least in my mind - would be a parity file application that is smart enough to look past the encodings, or rather incorporate them correctly. Any suggestions here?

---

### Post by ricardisimo on 2009-07-04
It would appear that either I have ceased to exist, or all of you have... including the developers of GPar2, who don't seem to be answering their emails. I've always suspected that I was my own personal thread killer, but this is ridiculous.

Can no one even speculate on a possible solution? Thanks.

---

### Post by ricardisimo on 2009-07-10
Here's this week's installment of my report from inside the singularity:

Not only can information not escape a black hole, it also evidently cannot get in either, or so this thread would suggest. I've posted in a spanish-language LoCo, hoping that someone there has had similar experiences with parity files and found a solution. No luck so far, and the developers don't respond to their emails.

Does this like a reportable bug? Should I go to Launchpad next?

---

### Post by ricardisimo on 2009-09-09
Since I'm having such a great time conversing with myself, it seems a shame not to share the good times with everyone. Gpar2 and PyPar2 are frontends only, and while the authors were kind enough to respond, they were not able to illuminate the basic problem, which would seem to be with par2. The developers of the latter have not responded.

When you installs Ubuntu, you select, among other things, a location and a keyboard layout. In my case it is always US International (AltGR Dead keys). My question is this: Does selecting a keyboard layout other than US Standard (or whatever it is called) set the entire system's character encoding to Western (ISO-8858-15) instead of UTF-8?

Is there some place to reset the default character encoding for the entire system without breaking anything? Thanks.

---

### Post by kung fu buntu on 2009-09-14
[I]The problem with your thread is that it gives to much information :p
Most people see "par2" in the thread title and run away from it since they don't know what that is :p

I've been searching for the perfect backup system, so I searched for "par2" in the thread title and ended up here :)[/I]


I don't know if this will work or not, since I haven't tested it myself. But that a look at this:
[http://chuchusoft.com/par2_tbb/download.html](http://chuchusoft.com/par2_tbb/download.html)
It seems to support directories, but I don't know about file encoding.


It's a shame linux/gnu/foss lack a update and reliable backup system.
(what can I say, it was made for server use, not for desktop)


About your question, I don't think the keyboard has anything to do with your locale.
You can change your locale settings, but I don't remember how.
When you change your locale, your text/filenames will appear different, and you may have to use a tool to convert the filename and text contents.

---

### Post by GrimJack on 2009-09-19
Firstly, you're not alone, Ricardisimo. I came across this thread via Google when trying to find a solution to the very same problem you're encountering. And I'll be subscribing to the thread to see if anything develops.

The issue is almost certainly with the par2 package. A bit of searching around the forums at [http://parchive.sourceforge.net/](http://parchive.sourceforge.net/) revealed:

> Yep, the PAR 1.0 spec definitely uses UTF-16 (although it does not make that clear).

I've just had a quick look at the PAR 2.0 and I see that the main part of the spec refers to ASCII (which is actually meaningless). The correct current name for what used to be known as ASCII is US-ASCII (which is a 7-bit character set).

par2cmdline and QuickPar treat the filename as 8-bit but leave it up to the OS to decide what character encoding is being used. When QuickPar accesses a file, the filename is treated as ANSI using whatever code page is currently selected as the default.

In the optional part of the PAR 2.0 spec where unicode is referred to, it gives no indication at all as to what encoding is used. I would assume that UTF-16 is intended.

Since Ubuntu is UTF-8 by default, I'd guess this is where the source of the issue lies.

---

### Post by ricardisimo on 2009-09-19
That is fascinating. I will be sending another inquiry to the developers with this added information included, and ask if there is either a workaround or an outright fix in the works. Thanks.

I'm going to go ahead and file a bug report. It doesn't always make a difference, but I think there is a little extra push when there is a formal report from the community. I'll link back to it here.

---

### Post by ricardisimo on 2009-09-19
Here it is: [https://bugs.launchpad.net/ubuntu/+source/par2cmdline/+bug/433260](https://bugs.launchpad.net/ubuntu/+source/par2cmdline/+bug/433260)
Please post your comments, as the more people express an interest, the more likely something will be done.

---

### Post by GrimJack on 2009-09-19
Take a look at this:

[http://manpages.ubuntu.com/manpages/jaunty/man1/convmv.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/convmv.1.html)

I installed the convmv package via Synaptic (It's not installed by default. Why would it be?) then used it to try to convert a filename with a special character to UTF-16, hoping this would let gpar2 (the par2 GUI I'm using) see the file and verify it along with the rest of the set of files I was checking.

The terminal, like everything else, is configured for UTF-8. When I issued the command, I copy/pasted the filename. (I don't know how to actually type the special characters and, as I've no real need to know, no interest in figuring out how.) When I pasted, the special character showed as I expected, but when I was asked to confirm the result of the change, the terminal was only able to display the "?-in-a-diamond" character in the filename. And the resulting change would have contained even more of them. Yikes!

It appears that the terminal was able to show me the special character when pasted from Nautilus, but when the terminal needed to present it back to me, it couldn't.

---

### Post by GrimJack on 2009-10-10
I've got a workaround for verifying files with foreign characters in the filenames that I found in the man page for par2.

> MISSNAMED AND INCOMPLETE DATA FILES
 
        If any of the recovery files or data files have the wrong filename, then par2 will not automatically find and scan them.
 
        To have par2 scan such files, you must include them on the command line when attempting to verify or repair.
 
        e.g.:
          par2 r test.mpg.par2 other.mpg
 
        This tells par2 to scan the file called other.mpg to see if it contains any data belonging to the original data files.
 
        If one of the extra files specified in this way is an exact match for a data file, then the repair process will rename the file so that it has the correct filename. 


So, I'm verifying a set of files where one file has a foreign character. I rename the file to eliminate the foreign character. Then I do the par2 check from the command line, appending the changed filename to the command as shown in the quote from the man page. Par2 will check the file and change the name to whatever it thinks it ought to be. Once it's checked and/or repaired, one could rename it to whatever one wants. The point is this works as far as checking and repairing the file itself.

Worked for me. Good luck!

---

### Post by hl2040 on 2009-10-16
GrimJack, thanks for that tip! Sometimes I don't read the manpage closely enough. That fixes many filename problems in par2.

That suggestion is great for misnamed PAR2/par2 files AND misnamed data files, which was my problem.

---

### Post by jonsson on 2010-02-09
Thanks, GrimJack. I found this thread and it solved my problem. :) I have a whole set of rar files with file names that par2 didn't like. This did the trick:
```
par2repair filename.par2 *.rar
```

---

### Post by ricardisimo on 2010-10-28
Whoa. What is "par2repair"? Is that part of par2?

GrimJack: Walk me through this, please, step-by-step. Suppose I have everything Arvo Pärt has ever done. Let's start with "Arvo Part - Arbos - 01 - Arbos.flac". What do I do? and if I have a folder with fifteen or twenty files associated with this album (jpegs, nfo, srr, etc.) is there any way around doing what you describe one file at a time? Thanks.

---

### Post by ricardisimo on 2010-11-16
Wow. These forums have really changed. I used to get immediate and multiple replies for even the stupidest questions. Now that I actually know what I'm doing and how to ask pointed questions: zilch.

---

### Post by frodon on 2010-12-07
Just to say i got the same issue with some french character, at the time i just opened virtualbox and launched my XP VM but off course this is not really a workaround.

I will post in the bug report too, thanks to GrimJack for the workaround :)

---

### Post by frodon on 2010-12-07
Just to say i got the same issue with some french character, at the time i just opened virtualbox and launched my XP VM but off course this is not really a workaround.

I will post in the bug report too, thanks to GrimJack for the workaround :)

---

### Post by ricardisimo on 2010-12-07
Could someone explain Grimjack's solution to me, in newb-speak? Let's suppose I have a song called "Chançon.mp3". How do I get the parity files generated for this file to recognize it? Thanks.

---

### Post by frodon on 2010-12-08
If you want to verify your file called "Chançon.mp3" with "Chançon.par2" checksum file then the command to use is :
```
par2 v Chançon.par2 Chançon.mp3
```
or if there are several files to use in your directory :
```
par2 v Chançon.par2 *.mp3
```

The trick is that par2 will take any file you give after the file to verify as extra/manually added file. Of course it would have been better if par2 took the right files alone but till we get a fix for this, it is the only workaround i think.

"par2 r" is the same thing than "par2repair" and the same is true for "par2 v" and "par2verify", these are 2 ways to write the same thing.

---

### Post by ricardisimo on 2010-12-08
Thank you very, very much. That only took a year-and-a-half, but if it works, I will be marking this thread as solved. Wish me luck!

P.S. - Commandline use of the par2 utility as you have posted here ("par2 v Chançon.par2 *.mp3") will apply to every file within the given folder, no?

---

### Post by frodon on 2010-12-09
Yes it will, all you have to do is to replace "*.mp3" by anything that match the files you want to check. "*.mp3" will just match all the files with ".mp3" extension in the current directory.

I still hope par2 can be fixed to ease character encoding issues.

---

### Post by GrimJack on 2010-12-09
It would be nice if par2 can be fixed. While this workaround gets the job done, it's time-consuming to implement.

Until it gets the attention it needs, I installed Wine and QuickPar, then configured Gnome to open .par2's with QuickPar. Performing the parity check is now just a double-click.

Which is what it ought to be on Ubuntu, regardless of character encoding.

---

### Post by ricardisimo on 2011-09-25
Do you guys think I should mark this as "solved" based on frodon's fix? Or is this really still a lingering problem with a workaround?

---

### Post by GrimJack on 2011-09-25
I would not call this issue solved because the workaround I found remains the only way to run the par2 check on files using a non-English character set. I haven't heard about par2 being updated or fixed, but I'm running the latest LTS release and I don't know if it was updated in more recent releases of Ubuntu.

I would call this solved if/when the workaround is no longer required.

---

### Post by ricardisimo on 2011-09-28
> **GrimJack said:**
> I would not call this issue solved because the workaround I found remains the only way to run the par2 check on files using a non-English character set. I haven't heard about par2 being updated or fixed, but I'm running the latest LTS release and I don't know if it was updated in more recent releases of Ubuntu.

I would call this solved if/when the workaround is no longer required.

That's right! It was you, not Frodon. Sorry about that. I agree, it's not really fixed until it's fixed, is it?

---

### Post by frodon on 2011-09-29
Maybe we can bump the bug report or try to contact the par2 developer directly.

The bug report has not been active till now unfortunately.

---

### Post by ricardisimo on 2012-01-15
Pathetic. Now I can't even get the workaround to function. I just keep getting that sort of man page/disclaimer:
```
par2cmdline version 0.4, Copyright (C) 2003 Peter Brian Clements.

par2cmdline comes with ABSOLUTELY NO WARRANTY.

This is free software, and you are welcome to redistribute it and/or modify
it under the terms of the GNU General Public License as published by the
Free Software Foundation; either version 2 of the License, or (at your
option) any later version. See COPYING for details.


Usage:

  par2 c(reate) [options] <par2 file> [files] : Create PAR2 files
  par2 v(erify) [options] <par2 file> [files] : Verify files using PAR2 file
  par2 r(epair) [options] <par2 file> [files] : Repair files using PAR2 files

You may also leave out the "c", "v", and "r" commands by using "parcreate",
"par2verify", or "par2repair" instead.

Options:

  -b<n>  : Set the Block-Count
  -s<n>  : Set the Block-Size (Don't use both -b and -s)
  -r<n>  : Level of Redundancy (%%)
  -c<n>  : Recovery block count (Don't use both -r and -c)
  -f<n>  : First Recovery-Block-Number
  -u     : Uniform recovery file sizes
  -l     : Limit size of recovery files (Don't use both -u and -l)
  -n<n>  : Number of recovery files (Don't use both -n and -l)
  -m<n>  : Memory (in MB) to use
  -v [-v]: Be more verbose
  -q [-q]: Be more quiet (-q -q gives silence)
  --     : Treat all remaining CommandLine as filenames

If you wish to create par2 files for a single source file, you may leave
out the name of the par2 file from the command line.
```
Anyone else experience this?

---

### Post by GrimJack on 2012-01-15
I haven't had any problems with the workaround. I suspect you have an error in the command you're using because the 'code' you've pasted is what par2 returns when there's a syntax problem. It would be helpful if we could see the exact command you're using.

---

### Post by ricardisimo on 2012-03-23
I'm pretty sure I did have a syntactical or spelling error somewhere. That's the problem with commandline workarounds, I guess.

I'm sorry, but I refuse to believe that this would take one of the developers more than five minutes to fix if she/he applied themselves. Very frustrating.

By the way, when RAR extracts from these "problem" rar files, it appends something like "(incorrect encoding)" to the end of the file it builds (rather than it's proper suffix, like ".mp4" or ".flac" or whatever). So it's not just PAR2 that has an issue with special characters. It's looking more like Linux has the issue. Not good.

---

### Post by rich1842 on 2012-07-31
ricardisimo: It will and won't be comforting for you to know that I am having exactly the same problem but cannot find a solution. Further it's impossible to rename or delete the files or to alter the permissions (where I am already the owner and the 'group' anyhow). I think it may be a handling error by something somewhere that cannot properly handle non-English alphabetics. Maybe because we have our locale set with English language and therefore English character-set. I have tried adding French as a second language (I think) but that doesn't seem to help.

[http://ubuntuforums.org/showthread.php?t=1236012&highlight=%26%2365533%3B]("http://ubuntuforums.org/showthread.php?t=1236012&highlight=%26%2365533%3B")

I just found the above with a recommendation that seems to work for others. I have used it but I still have the files with the characters and still can't change/delete them. I think they are built in now.

*****This really does work! Lets you delete these files.*****

'gksudo nautilus /home/carl/Desktop/' --- example - takes you to where your file/folder is.

[http://ubuntuforums.org/showthread.php?t=1123479](http://ubuntuforums.org/showthread.php?t=1123479)

That's where I got it.

'Warning: CRC32 mismatch in 04-gyorgy_ligeti--no._12_entrelacs.mp3. Decoded file probably corrupt.' is the error message I get.

I just d/l the same set on XP and it's fine - par files did their job etc. 

Just to see, I re-d/l on kubuntu pc and all the files are ok BUT when I  opened pypar2 to verify/repair I could see the 'bad' names in pypar2 (and stopped it).  So the par files and the data/music files are ok when I get them but the latter are being corrupted by pypar2. I can pass the files to XP to verify/repair but it's a pity linux doesn't seem to cope.

---

### Post by ricardisimo on 2012-08-01
Did you try frodon's commandline workaround from post #24? First cd to the pertinent folder, then use frodon's command.

---

### Post by rich1842 on 2012-08-01
Yes I did, and you can see below that the files were ok but are now corrupted by par2. I wonder where the smilies came from?

Loading "0 Ligeti - Keyboard Works.par2".
Loaded 60 new packets
Loading "0 Ligeti - Keyboard Works.vol001+002.PAR2".
Loaded 2 new packets including 2 recovery blocks
Loading "0 Ligeti - Keyboard Works.vol006+005.PAR2".
Loaded 5 new packets including 5 recovery blocks
Loading "0 Ligeti - Keyboard Works.vol134+128.PAR2".
Loaded 128 new packets including 128 recovery blocks
Loading "0 Ligeti - Keyboard Works.vol070+064.PAR2".
Loaded 64 new packets including 64 recovery blocks
Loading "0 Ligeti - Keyboard Works.vol011+009.PAR2".
Loaded 9 new packets including 9 recovery blocks
Loading "0 Ligeti - Keyboard Works.vol037+033.PAR2".
Loaded 33 new packets including 33 recovery blocks
Loading "0 Ligeti - Keyboard Works.vol000+001.PAR2".
Loaded 1 new packets including 1 recovery blocks
Loading "0 Ligeti - Keyboard Works.vol003+003.PAR2".
Loaded 3 new packets including 3 recovery blocks
Loading "0 Ligeti - Keyboard Works.vol020+017.PAR2".
Loaded 17 new packets including 17 recovery blocks

There are 29 recoverable files and 0 other files.
The block size used was 384000 bytes.
There are a total of 774 data blocks.
The total size of the data files is 290724336 bytes.

Verifying source files:

Target: "0 Ligeti - Keyboard Works - Kataeva, Aimard et al-wav.sfv" - missing.
Target: "0 Ligeti - Keyboard Works - Kataeva, Aimard et al.log" - missing.
Target: "0 Ligeti - Keyboard Works - Kataeva, Aimard et al.m3u" - missing.
Target: "0 auCDtect.txt" - missing.
Target: "0 cue (EAC range).cue" - missing.
Target: "0 cue (EAC tracks).cue" - missing.
Target: "0 scans.pdf" - missing.
Target: "01 Five Pieces for Piano 4-Hands (1) Indul&#65533; - Allegro.flac" - missing.
Target: "02 (2) Polif&#65533;n et&#65533;d - Allegro comodo.flac" - missing.
Target: "03 (3) H&#65533;rom lakodalmi t&#65533;nc - (a) A kapuban a szek&#65533;r - Allegro.flac" - missing.
Target: "04 - (b) Hopp ide tiszt&#65533;n - Andantino.flac" - missing.
Target: "05 - (c) Cs&#65533;ng&#65533; forg&#65533;s - Allegro.flac" - missing.
Target: "06 (4) Sonatina - (a) Allegro.flac" - found.
Target: "07 - (4) Andante.flac" - found.
Target: "08 - (b) Vivace.flac" - found.
Target: "09 (5) Allegro.flac" - found.
Target: "10 Capriccio #1- Allegretto capriccioso.flac" - found.
Target: "11 Invention - Risoluto.flac" - found.
Target: "12 Capriccio #2 - Allegro robusto.flac" - found.
Target: "13 Three Pieces for 2 Pianos (1976) (1) Monument.flac" - found.
Target: "14 (2) Selbstportrait mit Reich & Riley (& Chopin ist auch dabei).flac" - found.
Target: "15 (3)  In zart flie&#65533;ender Bewegung.flac" - missing.
Target: "16 Passacaglia ungherese - Andante.flac" - found.
Target: "17 Hungarian Rock (Chaconne, 1978) - Vivacissimo molto ritmico.flac" - found.
Target: "18 Continuum (1968) - Prestissimo.flac" - found.
Target: "19 Ricercare - Omaggio a Girolamo Frescobaldi.flac" - found.
Target: "20 2 Organ Studies (1) Harmonies - Rubato, sempre legatissimo.flac" - found.
Target: "21 (2) Coul&#65533;e - Prestissimo, sempre legato.flac" - missing.
Target: "22 Volumina (1961-62).flac" - found.

Scanning extra files:

File: "01 Five Pieces for Piano 4-Hands (1) Induló - Allegro.flac" - is a match for "01 Five Pieces for Piano 4-Hands (1) Indul&#65533; - Allegro.flac".
File: "02 (2) Polifón etüd - Allegro comodo.flac" - is a match for "02 (2) Polif&#65533;n et&#65533;d - Allegro comodo.flac".
File: "03 (3) Három lakodalmi tánc - (a) A kapuban a szekér - Allegro.flac" - is a match for "03 (3) H&#65533;rom lakodalmi t&#65533;nc - (a) A kapuban a szek&#65533;r - Allegro.flac".
File: "04 - (b) Hopp ide tisztán - Andantino.flac" - is a match for "04 - (b) Hopp ide tiszt&#65533;n - Andantino.flac".
File: "05 - (c) Csángó forgós - Allegro.flac" - is a match for "05 - (c) Cs&#65533;ng&#65533; forg&#65533;s - Allegro.flac".
File: "15 (3)  In zart fließender Bewegung.flac" - is a match for "15 (3)  In zart flie&#65533;ender Bewegung.flac".
File: "21 (2) Coulée - Prestissimo, sempre legato.flac" - is a match for "21 (2) Coul&#65533;e - Prestissimo, sempre legato.flac".

Repair is required.
7 file(s) have the wrong name.
7 file(s) are missing.
15 file(s) are ok.
You have 758 out of 774 data blocks available.
You have 262 recovery blocks available.
Repair is possible.
You have an excess of 246 recovery blocks.
16 recovery blocks will be used to repair.

Computing Reed Solomon matrix.
Constructing: done.
Solving: done.

Wrote 3774495 bytes to disk

Verifying repaired files:

Target: "0 Ligeti - Keyboard Works - Kataeva, Aimard et al-wav.sfv" - found.
Target: "0 Ligeti - Keyboard Works - Kataeva, Aimard et al.log" - found.
Target: "0 Ligeti - Keyboard Works - Kataeva, Aimard et al.m3u" - found.
Target: "0 auCDtect.txt" - found.
Target: "0 cue (EAC range).cue" - found.
Target: "0 cue (EAC tracks).cue" - found.
Target: "0 scans.pdf" - found.

Repair complete.
richard@slowpoke:~/ligeti$

---

### Post by ricardisimo on 2012-08-06
Not corrupted, just renamed, right? If par2 is happy with the files, then they're good. Just rename them to whatever you'd like at this point. I wasn't terribly happy with having ".bad file name" (or some such suffix) attached to my songs, but whatever. At least I know they downloaded correctly.

Par2 needs maintaining, but I doubt it's going to get it. Running the Windows alternative under wine might be your best bet.

---

### Post by rich1842 on 2012-08-07
Not quite - for me at least whenever I try to do anything with these files I get 'file does not exist' and they have no 'size' - I think they really don't exist properly.

Par2 tries to make files with these names but fails so I have 'empty' files with bad names (bad names causing the problem).

The 'original' files as d/l may or may not be ok but by letting par2 touch them things go wrong.

I suggest you should pass the files to a windoze (in this case I should say 'Windows') pc and check there with Quickpar. Quickpar will check and repair if needed then you can pass them back into ubuntu. Ubuntu seems to handle these names ok - it's only par2 that can't.

When you have used par2 are the original files not there with the original names? I find that when pypar2 repairs files (without the names we are talking about) it re-names the original with 'filename.mp3.1' but not in these cases. I think it starts out to repair but can't so leaves the original file untouched and creates as I said an 'empty' filename.

[Of course it's not pypar2 causing the problem - that is based on/uses par 2 where the real problem is.]

So what I am saying essentially is that your original d/l file MAY need repair but you would be best to keep those not the files with the new names - they are of no use.

That brings me to something else, the method I found of deleting these 'files' only seemed to work once. Can't get it to repeat it on this pc and can't get it to work on another. That's a bit strange...

---

### Post by ricardisimo on 2012-08-09
Tell me about it... very weird. Something else *way* beyond par2 appears to be going wrong on your machine.

---

