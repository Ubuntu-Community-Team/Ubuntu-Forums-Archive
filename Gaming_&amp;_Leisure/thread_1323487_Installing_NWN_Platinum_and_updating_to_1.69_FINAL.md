---
title: "Installing NWN Platinum and updating to 1.69 FINAL in Ubuntu 9.10"
date: 2009-11-11
forum: Gaming &amp; Leisure
---

### Post by Vidorin on 2009-11-11
Hello again, I had a thread a few distros ago when it was Ubuntu 8.10 I used the same method as described in the last thread and it ended up BREAKING 9.10. I tried three different methods still no go. I was dropped to corrupted orphaned inode files or whatever. Had to use the FSCK command when it dropped me to the root command prompt. I eventually fixed it and when I run NWN is when it goes *poof* Anyone know how I can install and make this game work properly in Ubuntu 9.10? Thank you in advance any help would be greatly appreciated. And on a side note how can I open rar and 7z files in Ubuntu? I can't figure out what application does that. Archive manager doesn't do it. Thanks again everyone. Also this is a Dell Latitude D600 Model laptop if that helps at all.

---

### Post by Perfect Storm on 2009-11-11
Try this: [http://gwos.org/doku.php/guides:64bit:nwn](http://gwos.org/doku.php/guides:64bit:nwn)


To open 7z: Install p7zip-full, it's in synaptic package manager. It will integrate with the already installed file extractor app.

---

### Post by oldrocker99 on 2009-11-12
I have found that Bioware's own method works perfectly for me:

[http://nwn.bioware.com/forums/viewtopic.html?topic=656261&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=656261&forum=72)

This method, which enables all the movies for the first time, worked for me when the several threads and installers I tried just didn't work at all. That said, the above link is useful, especially for 64-bit users.

I have installed it in my /home/games directory so as to have no permission problems, It runs perfectly in Linux and runs all the Neverwinter Vault modules, making this unquestionably the most RPG in a box. 

A few hints:

Although case doesn't seem to matter in the other games directories, filenames in the hak directory MUST be in lowercase (the exception is apparently Bioware's own hak files).

Some Vault modules are only available as .exe files, which can be opened and extracted using File Roller (GNOME's default archive manager).

If the game is new to you, do examine the 100% free modules at Neverwinter Vault

[http://nwvault.ign.com/](http://nwvault.ign.com/)

Starting with a character creator and just about any of the Hall of Fame modules will get you rolling. Of the installed modules, the original is about the weakest. The second is much better, and the third is pretty close to terrific. Kingmaker (which the above Bioware link tells you how to install) is intensive role-playing and very well-written.

I've been playing this game for 7 years now and it's just as good (in fact, better--no disk needed, for one thing) in Linux as in Windows.

It didn't break MY 9.10 installation.

:guitar:

---

### Post by Vidorin on 2009-11-12
Alright I went to that link and that is for the Diamond Edition when I own the original being the 3 disc NWN then 1 disc SOU and the 1 Disc HOTU and  4 CD Platinum editions of the game. I found these instructions for the Platinum Edition of the game on that forum.[http://nwn.bioware.com/forums/viewtopic.html?topic=641740&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=641740&forum=72)  
And it seems when I use the ./nwn command is when it takes a ****. I log out of the game and Ubuntu's GUI takes a dump and I have to run the fsck command because it messes up the inode list. Also when I tried to follow the putting in the CD key part it just keeps asking for the NWN Original key I did it about twenty times.. so then I just skipped the putting in the key part and then copied over the nwncdkey.ini file in there and it went into the game I was able to use it. I'm going to try and play it as my next step but when I exit the game my Ubuntu takes a ****. That's when I have to force restart it and use fsck to repair it and make it work correctly again.

---

### Post by oldrocker99 on 2009-11-12
Dude, the Diamond Edition costs $20; why don't you get it?

:guitar:

---

### Post by Vidorin on 2009-11-12
Why should I have to purchase another copy of the game when I already own two of them? I'm trying to solve a problem not toss money at it not to mention I can't afford it at the moment. Anyway, I tried Artificial Intelligence's instructions to the letter same problem yet again. I'm thinking it's one of two things either Ubuntu lost the ability (that it never seemed to really have to begin with because gaming has always been a Linux issue) to play a simple game in 9.10 which I seriously doubt it lost the little ability it had to do so. Or my upgrade got pooched somewhere along the line because I did the kernel upgrade via the GUI updater. I was at 8.10 and it updated to 9.10 or did I have 9.4 I can't remember. But in any event I think the next logical step here is for me to try and reformat with a fresh install of Ubuntu 9.10 on this thing and another shot at reinstalling NWN. I will admit I'm beginning to lose my patience. See the error is when it pooches the GUI to Ubuntu and then it gives me the inode errors and needs me to run FSCK at the recovery prompt when it's at the root level. I can't do anything really the GUI locks up. Then when I try to restart it I have to hold the power button and force it. Or if I hit the power button it asks me what to do and I get the clear blocks for characters and the paper with the red x on it for the images. And thats when it drops me to that prompt. It hasn't been doing so because I usually restart it quick and it then "rights" itself or so it seems and starts up normally and works correctly but I have no issues until I try and run NWN and thats when it does it all over again.

---

### Post by Vidorin on 2009-11-13
Alright an update here I reinstalled Ubuntu 9.10 from a fresh install and then followed Artificial Intelligence's instructions to the letter and it works. Now I've encounted two more slight issues. Problem number 1 when I exit the game "normally" it seems to hang at a black screen with the NWN mouse pointer where I can't move it. I've force restarted the computer via the power button seems the only way to get out of it. And Problem number 2 where exactly did those instructions install the physical game Artificial? Because I'd like to add the haks and so forth for the whitewolf server I play on. I did a search on the filesystem for nwn and neverwinter I couldn't find anything. So where did those commands install the game?

---

### Post by Perfect Storm on 2009-11-14
in ~/.Games/nwn
It's in your home directory.
You can see .Games if you set your file browser to see hidden files.


Problem 1 you have I'm not sure about. But you might check nwns error log (~/.Games/nwn).

---

### Post by Naegling23 on 2009-11-18
I cant seem to get the movies to play, the game starts up fine with the part enabled in the nwn startup script, I can click on any of the movies in the game menu, but when I do, nothing happens.  Here is my terminal output if anyone can find any details

pangolin@ubuntu:~/nwn$ ./nwn
NOTICE: NWMovies(./nwmain): Version: 20090223.080954
NOTICE: Looking up symbols in libSDL.....
NOTICE: NWMovies: using libSDL via direct dlopen()
NOTICE: SDL Library determined to be: ./lib/libSDL-1.2.so.0
NOTICE: NWMovies: SDL_WM_GrabInput() address: f7523900
NOTICE: NWMovies: SDL_GetVideoSurface() address: f7521048
NOTICE: NWMovies: SDL_WM_ToggleFullScreen() address: f75239e8
NOTICE: NWMovies: SDL_PollEvent() address: f753d51c
NOTICE: NWMovies: SDL_WM_IconifyWindow() address: f75239a8
NOTICE: NWMovies: Patch 0 Address: 0x08077a9d
NOTICE: NWMovies: Patch 1 Address: 0x08077ab1
NOTICE: NWMovies: Patch 2 Address: 0x0815b5f7
NOTICE: NWMovies: Patch 3 Address: 0x0815b611
NOTICE: NWMovies: Patch 4 Address: 0x0807796f
NOTICE: NWMovies: Patch 5 Address: 0x08207835
NOTICE: NWMovies: Patch 6 Address: 0x08207858
NOTICE: NWMovies: PrePatch0: 8b 80 78 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch1: 8b 80 7c 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch2: e8 68 c5 f1 ff 83 ec 08 
NOTICE: NWMovies: PrePatch3: 169+: eb 59 90 83 
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08 
NOTICE: NWMovies: PostPatch3: 169+: 90 90 90 83 
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53 
NOTICE: NWMovies: PostPatch4: e9 20 64 6e ef 
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 72 4f 2a 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c 
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
NOTICE: NWMovies: Initialized.
NOTICE: SDL_WM_GrabInput(QUERY) called..
NOTICE: SDL_WM_GrabInput(OFF) called..
pangolin@ubuntu:~/nwn$

---

### Post by Perfect Storm on 2009-11-18
As far as the movies go in NWN, it's a hit or miss situation. I never got the movies to work.

---

### Post by oldrocker99 on 2009-11-18
I had the movies working in 8.10, but the Bink Movie Player depends on libstdc++5 - The GNU Standard C++ Library v3, which is apparently not available in the 9.10 repos. I found a .deb of the library, but I get

ERROR: ld.so: object './nwmovies.so' from LD_PRELOAD cannot be preloaded: ignored.

when I run ./nwn. 

Oh, well.

:guitar:

---

### Post by Naegling23 on 2009-11-19
oh well,  I had hoped I could get them working in game....anyway, is there a way to watch them out of game?  I have also heard about possibly converting them to mpeg or some other file format so that mplayer can handle the video, would this work?

---

### Post by Naegling23 on 2009-11-19
well, I got them working, or one of them at least.

in your nwn directory, open the file nwmovies.pl

now, scroll down until you see:

# $mplayer = "";
# $plaympeg = "";
# $binkplayer = "";

remove the # from in front of $binkplayer so it reads

# $mplayer = "";
# $plaympeg = "";
 $binkplayer = "";

now, go to [http://www.youtube.com/watch?v=emX88IT7YnY&feature=related](http://www.youtube.com/watch?v=emX88IT7YnY&feature=related)

download any one of the movies.  Move it into the movies folder, and rename it as one of the files, but with an extension that mplayer will recognize...I downloaded it as .mp4, but anything should work.

The movie plays using mplayer just fine.

Now, the problem is that I am lazy, and do not want to do this for all of the movies...anyone want to put some of the work into converting all of the movies?

-mods, if this is illegal, please let me know, and I will remove the post.

---

