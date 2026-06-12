---
title: "Conky + Amarok Lyrics Help"
date: 2008-12-16
forum: General Help
---

### Post by too5hort on 2008-12-16
Hi, recently installed conky and got a nice touch of it, now i want to ad a lyric displayer to it, and i dont know how to do that. I have my conky set up to the right of the screen and i would like the lyrics to show up on the left side of conky.

I found a scriptbut i dont know if its working and how to install it and make it work.
[http://gnome-look.org/content/show.php/Lyricsdownloader+for+Conky?content=94262](http://gnome-look.org/content/show.php/Lyricsdownloader+for+Conky?content=94262)

Can anyone please give as much details and help on this problem.

Best Regards too5hort !

---

### Post by unutbu on 2008-12-16
Download the Ubuntu deb file on the page you posted.
Then navigate to the file called "lyricsdownloader_0.8.3.deb" and double-click on it. This should install the following files:

```

/usr/share/doc/lyricsdownloader/README
/usr/share/doc/lyricsdownloader/conkylyrics
/usr/local/bin/lyricsdownloader

```

Copy /usr/share/doc/lyricsdownloader/conkylyrics to your home directory and rename it .lyrics_conkyrc

To get the lyrics displayed on your root window, run conky this way:
```

conky ~/.lyrics_conkyrc
```

---

### Post by too5hort on 2008-12-16
When i try to open the .deb package it says 

ERROR: Wrong architecture 'i386'

But if you can guide me with the .tar.bz2 package?

---

### Post by unutbu on 2008-12-16
Okay, the instructions below assume you've downloaded the tar.bz2 file to your home directory. 

Open a terminal (Applications>Accessories>Terminal) and type
```

tar xvjf lyricsdownloader_0.8.3.tar.bz2
```

This command extracts the contents of the tar.bz2 archive.
You should see
```

lyricsdownloader/
lyricsdownloader/README
lyricsdownloader/.conkylyrics
lyricsdownloader/lyricsdownloader.py
```

Now type
```

cp lyricsdownloader/.conkylyrics ~
```

This copies the "conkyrc" file to your home directory. We don't want to call this ~/.conkyrc since it sounds like you have already made a conkyrc, and we don't want to overwrite it.

Next, 
```

mkdir ~/bin
cp lyricsdownloader/lyricsdownloader.py ~/bin
```

Test that lyricsdownloader.py is working by playing a song and then typing
```

lyricsdownloader.py
```

You should see the lyrics of the song spilled onto your terminal.
If you see an error message, post it. If you see nothing, it may be because your song file's artist and title tags are messed up, mispelled, or because [http://lyricwiki.org](http://lyricwiki.org) doesn't have lyrics for your song. ([http://lyricwiki.org](http://lyricwiki.org) is the site that lyricsdownloader.py uses to grab lyrics from the web.) Anyway, if you run into trouble, post the artist and title and which music app you are using (e.g. exaile, amarok, mpd, etc).

If you see lyrics then the last step is to type
```

conky ~/.conkylyrics
```

This command will start a conky process which is configured by .conkylyrics.
I might be able give you instructions on how to get this to launch when you start your music player, if you want. If you'd like help doing this, please post which music player you use and your preferred method of launching the music player (e.g. double-clicking a launcher, using the gnome panel menu, terminal, etc.)

---

### Post by too5hort on 2008-12-16
When i type lyricsdownloader.py in terminal it says 
bash: lyricsdownloader.py: kommandot finns inte

The command instn existing

---

### Post by unutbu on 2008-12-16
Please post:

```
grep -i -A5 -B5 'path' ~/.profile
echo $PATH
ls -l ~/bin
ls -l ~/lyricsdownloader

```

---

### Post by too5hort on 2008-12-16
jesper@ubuntu:~$ grep -i -A5 -B5 'path' ~/.profile
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
jesper@ubuntu:~$ echo $PATH
/home/jesper/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
jesper@ubuntu:~$ ls -l ~/bin
totalt 8
-rwxr-xr-x 1 jesper jesper 8019 2008-12-16 22:50 lyricsdownloader.py
jesper@ubuntu:~$ ls -l ~/lyricsdownloader


-rwxr-xr-x 1 jesper jesper 8019 2008-12-13 23:18 lyricsdownloader.py
-rw-r--r-- 1 jesper jesper  509 2008-12-13 23:10 README

---

### Post by unutbu on 2008-12-16
Your .profile looks fine.
Your $PATH looks good.
lyricsdownloader.py is in the right place, and has the executable bit set.

How about try this:

type 

```
lyric[TAB]
```

When you press the TAB key, the command should be autocompleted.

If that doesn't work, try closing your terminal and opening a new one. 

If that doesn't work, try logging out and the logging back in.

---

### Post by too5hort on 2008-12-16
Did what you wrote, even restarted my computer, the only thing that happens is when i type that is that the terminal thinks for about 1 sek and then displaying 

jesper@ubuntu:~$

(The [TAB] thing works btw)

---

### Post by unutbu on 2008-12-16
Okay, that means lyricsdownloader.py was launched, it tried to download the lyrics from 
[http://lyricwiki.org](http://lyricwiki.org) but couldn't find lyrics for the song you are playing.

Point you browser here:
```

http://lyricwiki.org/api.php?artist=THE+ARTIST&song=THE+SONG+TITLE&fmt=text
```

Change THE+ARTIST to the real artist, replacing spaces with plus signs.
Change THE+SONG+TITLE with the real title, replacing spaces with plus signs.

Can you find lyrics for your song? 

If you can find the lyrics on the lyricwiki.org website, then take note of the artist and title, and then go into amarok and make sure the artitst and title tags are exactly the same. Edit them if need be.

Then run lyricsdownloader.py again.

If you can't find the lyrics on lyricwiki.org, that explains why lyricsdownloader.py is not working. There is a way around this however: If you can find the lyrics from another source, then you can copy those lyrics and put them in ~/.lyrics. This is a directory that lyricsdownloader.py searches before trying to download lyrics from lyricwiki.org. It also saves lyrics that it finds in this directory.

Put the lyrics text file in a file whose path is ~/.lyrics/ARTIST/TITLE.lyric

(Change ARTIST and TITLE to the appropriate values -- they should match the artist and title tags in your mp3 file).

Then edit ~/.lyrics/missingsongs.txt. Take out the line that lists the "ARTIST : TITLE".

Just to check that the overall conky+lyricsdownloader.py system is working, try playing some more songs and see if lyricsdownloader.py can find any of them.

---

### Post by too5hort on 2008-12-16
Hmm, i found the lyric on the website, and i cheked so the tags are the same in amarok but still no lyricshower on the display.

Maybe i should at some lines of something to get the lyric text to show up on the desktop?

---

### Post by unutbu on 2008-12-16
Let's try this:
Edit ~/bin/lyricsdownloader.py:
Search for these lines about 3/4 of the way down:
[PHP]
#make names lowercase for folders and remove trailing newlines
try:
    artistname = artistname.strip().lower()
    songname = songname.strip().lower()
except:
    sys.exit(1)
[/PHP]

Add the following two lines right after "sys.exit(1)":

[PHP]
print artistname
print songname
[/PHP]
Python is sensitive to indention. Make sure there are no spaces in front of the lines you add.

Play the song using amarok.
Then run 
```

lyricsdownloader.py
```
It should report the artist and the title of the song.
Please post the output. 

What is the url on lyricwiki.org?

---

### Post by too5hort on 2008-12-17
```
#make names lowercase for folders and remove trailing newlines
try:
    artistname = artistname.strip().lower()
    songname = songname.strip().lower()
except:
    sys.exit(1)
print artistname
print songname  

```

And when i type lyricsdownloader in terminal it gives me 

```
jesper@ubuntu:~$ lyricsdownloader.py 
  File "/home/jesper/bin/lyricsdownloader.py", line 27
    artistname = amarokplayer.GetMetadata(print artistname

```

[http://lyricwiki.org/api.php?artist=MGMT&song=Kids&fmt=text](http://lyricwiki.org/api.php?artist=MGMT&song=Kids&fmt=text)

Thats one of the song im trying with mostly.

---

### Post by unutbu on 2008-12-17
You've put the print statement on line 27. It should be on line 219 (or thereabouts):
```
    artistname = amarokplayer.GetMetadata([COLOR="Red"]print artistname[/COLOR]
```

Remove the edits that you made and try again.

---

### Post by too5hort on 2008-12-17
Same as before, terminal thinks and then pops me to ```
jesper@ubuntu:~$ lyricsdownloader.py 
jesper@ubuntu:~$ 

```

Tried playing music in Rhythmbox and typed in lyricsdownloader.py in terminal and then it worked, guess i can live with rhythmbox, but how do i get the lyrics to display on the dektop?

---

### Post by unutbu on 2008-12-17
There appears to have been a bug concerning Amarok that was fixed on 2008-12-13: [http://code.google.com/p/lyricsdownloader/updates/list](http://code.google.com/p/lyricsdownloader/updates/list)

Here is the latest version of the lyricsdownloader script:
[http://lyricsdownloader.googlecode.com/svn/trunk/lyricsdownloader.py](http://lyricsdownloader.googlecode.com/svn/trunk/lyricsdownloader.py)

Make a backup copy of your current lyricsdownloader.py:

```

mv ~/bin/lyricsdownloader.py ~/bin/lyricsdownloader_bak.py
```
Save [http://lyricsdownloader.googlecode.com/svn/trunk/lyricsdownloader.py](http://lyricsdownloader.googlecode.com/svn/trunk/lyricsdownloader.py) in ~/bin/lyricsdownloader.py

Make it executable:
```

chmod +x ~/bin/lyricsdownloader.py
```

Some of these commands are rather long. Using the mouse and copy/paste may help.


To get the lyrics to appear on the desktop, type
```

conky ~/.conkylyrics
```
(see the end of [http://ubuntuforums.org/showpost.php?p=6381959&postcount=4](http://ubuntuforums.org/showpost.php?p=6381959&postcount=4))

---

### Post by too5hort on 2008-12-17
```
jesper@ubuntu:~$ dcop amarok player artist
Eels
jesper@ubuntu:~$ dcop amarok player title
Hey Man (Now You're Really Living)
jesper@ubuntu:~$ 

```

Thats the current song im trying with.

---

### Post by too5hort on 2008-12-17
How do i get the amarok update?

---

### Post by unutbu on 2008-12-17
Copy and paste these commands into the terminal:
```

mv ~/bin/lyricsdownloader.py ~/bin/lyricsdownloader_bak.py
wget "http://lyricsdownloader.googlecode.com/svn/trunk/lyricsdownloader.py" -O ~/bin/lyricsdownloader.py
chmod +x ~/bin/lyricsdownloader.py
conky ~/.conkylyrics

```
Play a song using Amarok. Do the lyrics show up on the background?

---

### Post by too5hort on 2008-12-17
Problems fixed, great help man, thank you

---

### Post by erictherev on 2008-12-29
I'm trying to follow these directions to get this working on my wife's system.

First, you should probably know that I'm attempting everything I've done so far via ssh. Also, all of my music files are stored remotely in my Ubuntu system and are being played over smb.

Here's what I've done and what I've gotten since installing using GDebi:

```
lupa@Korriban:~/.conkyfiles$ mkdir ~/bin
lupa@Korriban:~/.conkyfiles$ cp lyricsdownloader/lyricsdownloader.py ~/bin
cp: cannot stat `lyricsdownloader/lyricsdownloader.py': No such file or directory
lupa@Korriban:~/.conkyfiles$ lyricsdownloader.py
-bash: lyricsdownloader.py: command not found
lupa@Korriban:~/.conkyfiles$ lyricsdownloader
ERROR: Couldn't attach to DCOP server!
ERROR: Couldn't attach to DCOP server!
Traceback (most recent call last):
  File "/usr/local/bin/lyricsdownloader", line 207, in <module>
    artistname = artistname.strip().lower()
NameError: global name 'artistname' is not defined
lupa@Korriban:~/.conkyfiles$ dcop amarok player artist
ERROR: Couldn't attach to DCOP server!

```

I figured out that lyricsdownloader wasn't installed in ~/bin, so I found it and put it there. Here's the rest of what I've done since originally posting here:

```
lupa@Korriban:~/bin$ chmod +x ~/bin/lyricsdownloader.py
lupa@Korriban:~/bin$ lyricsdownloader
-bash: /usr/local/bin/lyricsdownloader: No such file or directory
lupa@Korriban:~/bin$ lyricsdownloader.py
-bash: lyricsdownloader.py: command not found
lupa@Korriban:~/bin$ python lyricsdownloader.py
ERROR: Couldn't attach to DCOP server!
ERROR: Couldn't attach to DCOP server!
Traceback (most recent call last):
  File "lyricsdownloader.py", line 207, in <module>
    artistname = artistname.strip().lower()
NameError: global name 'artistname' is not defined

```

Any help here is greatly appreciated.

---

### Post by erictherev on 2008-12-29
OK, what's really odd here is that while I get an error when I do the following over ssh:

```
lupa@Korriban:~$ dcop amarok player artist
```

I get the following:

```
ERROR: Couldn't attach to DCOP server!
```

However, when conky does the exact same thing, I get the desired output on my wife's monitor.

:confused:

Here's the conky code that currently works on her system:

```
${font Sonora:size=32}${color #E6E8FA}V${color #BF3EFF}${font Knights Quest:size=16} MUSIC ${hr 2}$color
${color #00FF00}${font Arial:size=10}${alignc}${if_running amarokapp}${execi 10 dcop amarok player artist} - ${execi 10 dcop amarok player title}$endif
${color #00FF00}${font Arial:size=10}${alignc}${if_running amarokapp}${execi 1 dcop amarok player currentTime} / ${execi 10 dcop amarok player totalTime}$endif
```

Following other directions listed in this thread:

```
lupa@Korriban:~$ grep -i -A5 -B5 'path' ~/.profile
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
lupa@Korriban:~$ echo $PATH
/home/lupa/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
lupa@Korriban:~$ ls -l ~/bin
total 8
-rwxr-xr-x 1 lupa lupa 7821 2008-12-28 15:55 lyricsdownloader.py
lupa@Korriban:~$ ls -l ~/lyricsdownloader
ls: cannot access /home/lupa/lyricsdownloader: No such file or directory
```

---

### Post by eightmillion on 2008-12-30
> **erictherev said:**
> OK, what's really odd here is that while I get an error when I do the following over ssh:

```
lupa@Korriban:~$ dcop amarok player artist
```

I get the following:

```
ERROR: Couldn't attach to DCOP server!
```

However, when conky does the exact same thing, I get the desired output on my wife's monitor.

:confused:

Here's the conky code that currently works on her system:

```
${font Sonora:size=32}${color #E6E8FA}V${color #BF3EFF}${font Knights Quest:size=16} MUSIC ${hr 2}$color
${color #00FF00}${font Arial:size=10}${alignc}${if_running amarokapp}${execi 10 dcop amarok player artist} - ${execi 10 dcop amarok player title}$endif
${color #00FF00}${font Arial:size=10}${alignc}${if_running amarokapp}${execi 1 dcop amarok player currentTime} / ${execi 10 dcop amarok player totalTime}$endif
```

Following other directions listed in this thread:

```
lupa@Korriban:~$ grep -i -A5 -B5 'path' ~/.profile
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
lupa@Korriban:~$ echo $PATH
/home/lupa/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
lupa@Korriban:~$ ls -l ~/bin
total 8
-rwxr-xr-x 1 lupa lupa 7821 2008-12-28 15:55 lyricsdownloader.py
lupa@Korriban:~$ ls -l ~/lyricsdownloader
ls: cannot access /home/lupa/lyricsdownloader: No such file or directory
```

I think your problem is that you're trying to connect to the DCOP server over ssh. You have to be the user running the DCOP server or a superuser to do that.

---

### Post by erictherev on 2008-12-30
> **erictherev said:**
> ```
lupa@Korriban:~$ ls -l ~/lyricsdownloader
ls: cannot access /home/lupa/lyricsdownloader: No such file or directory
```

> **eightmillion said:**
> I think your problem is that you're trying to connect to the DCOP server over ssh. You have to be the user running the DCOP server or a superuser to do that.

I tried to connect to the DCOP from a terminal at my wife's computer with the exact same results.

---

### Post by eightmillion on 2008-12-30
> **erictherev said:**
> I tried to connect to the DCOP from a terminal at my wife's computer with the exact same results.

That is strange. Could you try installing python-dcop and running this script? I'm considering changing the way I hit dcop with lyricsdownloader.

---

### Post by erictherev on 2008-12-30
> **eightmillion said:**
> That is strange. Could you try installing python-dcop and running this script? I'm considering changing the way I hit dcop with lyricsdownloader.

I installed python-dcop and then ran your script. From my wife's computer I got the artist and title of the song that was playing. When I tried it over ssh, I got the following (I hope it helps):

```
root@Korriban:/home/lupa/.conkyfiles# python amarok.py
ASSERT: debug output not ended with \n
[
0: /usr/lib/libkdecore.so.4(_Z11kdBacktracei+0x49) [0x7f55495151b9]
1: /usr/lib/libkdecore.so.4(_Z11kdBacktracev+0xe) [0x7f554951544e]
2: /usr/lib/libkdecore.so.4(_ZN10kdbgstreamD1Ev+0x82) [0x7f5549558262]
3: /var/lib/python-support/python2.5/pcop.so(_ZN10PythonDCOP6Client4dcopEv+0x79) [0x7f5549ad6069]
4: /var/lib/python-support/python2.5/pcop.so(_ZN10PythonDCOP9dcop_callEP7_objectS1_+0x1cd) [0x7f5549ad736d]
5: python(PyEval_EvalFrameEx+0x661b) [0x48964b]
6: python(PyEval_EvalCodeEx+0x776) [0x48a406]
7: python [0x4d528a]
8: python(PyObject_Call+0x13) [0x417e33]
9: python [0x41e66f]
10: python(PyObject_Call+0x13) [0x417e33]
11: python [0x45b084]
12: python(PyObject_Call+0x13) [0x417e33]
13: python(PyEval_EvalFrameEx+0x314a) [0x48617a]
14: python(PyEval_EvalCodeEx+0x776) [0x48a406]
15: python(PyEval_EvalCode+0x32) [0x48a522]
16: python(PyRun_FileExFlags+0x10e) [0x4abe2e]
17: python(PyRun_SimpleFileExFlags+0x1a9) [0x4ac0c9]
18: python(Py_Main+0x8fd) [0x4145ad]
19: /lib/libc.so.6(__libc_start_main+0xf4) [0x7f5549cfc1c4]
20: python [0x413b29]
]
WARNING: Could not attach to DCOP server
Traceback (most recent call last):
  File "amarok.py", line 7, in <module>
    print rok.artist(), rok.title()
  File "/var/lib/python-support/python2.5/pydcop.py", line 90, in __call__
    return pcop.dcop_call( self.appname, self.objname, self.name, args )
RuntimeError: Object is not accessible.

```

---

### Post by erictherev on 2008-12-30
Completely skipping ssh, here is what I am currently working with when I am at my wife's computer:

```
lupa@Korriban:~/bin$ python lyricsdownloader.py
Traceback (most recent call last):
  File "lyricsdownloader.py", line 215, in <module>
    artistname = artistname.strip().lower()
NameError: global name 'artistname' is not defined
```

I am still getting the artist name, song title and length from dcop in conky.

---

### Post by eightmillion on 2008-12-30
> **erictherev said:**
> Completely skipping ssh, here is what I am currently working with when I am at my wife's computer:

```
lupa@Korriban:~/bin$ python lyricsdownloader.py
Traceback (most recent call last):
  File "lyricsdownloader.py", line 215, in <module>
    artistname = artistname.strip().lower()
NameError: global name 'artistname' is not defined
```

I am still getting the artist name, song title and length from dcop in conky.

Could you try this newer version of lyricsdownloader. This one tries to import python-dcop and use that to get the info, and if it fails, it falls back to the old method.

---

### Post by erictherev on 2008-12-30
With the newer version:

```
lupa@Korriban:~/bin$ python lyricsdownloader.py
Traceback (most recent call last):
  File "lyricsdownloader.py", line 264, in <module>
    else: main()
  File "lyricsdownloader.py", line 206, in main
    app = checkrunning()
  File "lyricsdownloader.py", line 200, in checkrunning
    if not app:
UnboundLocalError: local variable 'app' referenced before assignment
```

---

### Post by eightmillion on 2008-12-30
> **erictherev said:**
> With the newer version:

```
lupa@Korriban:~/bin$ python lyricsdownloader.py
Traceback (most recent call last):
  File "lyricsdownloader.py", line 264, in <module>
    else: main()
  File "lyricsdownloader.py", line 206, in main
    app = checkrunning()
  File "lyricsdownloader.py", line 200, in checkrunning
    if not app:
UnboundLocalError: local variable 'app' referenced before assignment
```

Yeah, I uploaded the wrong version the first time, but I went back and edited it. You need to redownload.

---

### Post by erictherev on 2008-12-30
With the updated script:

```
lupa@Korriban:~/.conkyfiles/scripts$ python lyricsdownloader.py
Traceback (most recent call last):
  File "lyricsdownloader.py", line 214, in <module>
    artistname = artistname.strip().lower()
NameError: global name 'artistname' is not defined

```

To reiterate, at this point I am no longer attempting any of this via ssh.

---

### Post by erictherev on 2008-12-30
Python version:

```
lupa@Korriban:~/.conkyfiles/scripts$ python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:31:22)
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>     
```

---

### Post by eightmillion on 2008-12-31
> **erictherev said:**
> With the updated script:

```
lupa@Korriban:~/.conkyfiles/scripts$ python lyricsdownloader.py
Traceback (most recent call last):
  File "lyricsdownloader.py", line 214, in <module>
    artistname = artistname.strip().lower()
NameError: global name 'artistname' is not defined

```

To reiterate, at this point I am no longer attempting any of this via ssh.

I don't think there's anything more that I can do. Have you considered upgrading to Amarok 2?

---

### Post by erictherev on 2009-01-01
> **eightmillion said:**
> I don't think there's anything more that I can do. Have you considered upgrading to Amarok 2?

I searched the repos for amarok 2 with no luck. Has it been released for 64-bit yet?

---

### Post by eightmillion on 2009-01-01
> **erictherev said:**
> I searched the repos for amarok 2 with no luck. Has it been released for 64-bit yet?

The package is amarok-kde4. Try: sudo aptitude install amarok-kde4

---

### Post by wynneth on 2009-02-21
It seems I am having generally the same problem as erictherev was (minus the ssh). I installed lyricsdownloader and keep getting the
```

Traceback (most recent call last):
  File "/usr/local/bin/lyricsdownloader", line 207, in <module>
    artistname = artistname.strip().lower()
NameError: global name 'artistname' is not defined

```
error.
I went into the script and removed all unecessary lines so I could try to pin it down a little better (HA! I know ZIP about python, just what I've picked up messing with conky lately.)
Basically I took it down to just having the getamarokapp function, because that's the one that SHOULD work for me. I know for a fact ```
dcop amarok player artist
``` works because I can do it from terminal. If I try ```
artistname = str(os.popen("dcop amarok player artist","r").read())
``` I get an error ```
bash: syntax error near unexpected token `('
``` What's going on here? I can write a bash script to define artistname via ```
artistname=`dcop amarok player artist`
``` but we're in python so I don't have a clue what you're doing here.

Haaaaaalp I really like your script!

---

### Post by eightmillion on 2009-02-21
Hi Wynneth,

Could you try the svn version of lyricsdownloader out? You can get it from svn by entering the command 'svn checkout [http://lyricsdownloader.googlecode.com/svn/trunk/](http://lyricsdownloader.googlecode.com/svn/trunk/) lyricsdownloader' or you can grab it from [this link.]("http://code.google.com/p/lyricsdownloader/source/browse/trunk/lyricsdownloader.py") It has a -v option that should be helpful for debugging. Also, could you try some commands out:

```
pgrep amarokapp
```

```
python -c 'import pydcop;print pydcop.DCOPObject( "amarok", "player" ).artist()'
```

```
python -c 'import os;print str(os.popen("dcop amarok player artist","r").read())'
```

---

### Post by wynneth on 2009-02-21
Code snippet one does reveal the PID of amarok. Code snippet two fails with ```
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named pydcop
``` Code snippet three properly displays the currently playing artist name.
It seems like basically the function is working properly but for some reason it isn't passing to the artistname variable. It fails everytime at the first call of artistname, which is in ```
artistname = artistname.strip().lower()
```
Using the svn I get two lines that say ```
no such function
``` and then the lyrics. The verbose output of the svn is ```
Found player: amarok
Traceback (most recent call last):
  File "/usr/local/bin/lyricstest2", line 755, in <module>
    main()
  File "/usr/local/bin/lyricstest2", line 684, in main
    a = player()
  File "/usr/local/bin/lyricstest2", line 56, in __init__
    self.rok = self.bus.get_object('org.kde.amarok','/Player')
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.kde.amarok was not provided by any .service files

```

We're so close, I hope this is something you'll look at and go, "Oh, add a ; here" LOL :D

---

### Post by eightmillion on 2009-02-21
The problem is it thinks you're running amarok 2.x. Try changing line 30 from:

```
        self.players = [ 'amarok','amarokapp','rhythmbox','audacious','banshee-1',
```

to:

```
        self.players = [ 'amarokapp','rhythmbox','audacious','banshee-1',
```

---

### Post by wynneth on 2009-02-21
Hmm. I changed that in the SVN and I get ```
wynneth@wilykat:~$ lyricsdownloaderSVN  -v
Found player: amarokapp
no such function
no such function
Artist: Darude
        Songname: Calm Before The Storm

Lyrics file already exist for: darude  :  calm before the storm
```
So now we're working but I still get the no such function before everything.

---

### Post by eightmillion on 2009-02-21
> **wynneth said:**
> Hmm. I changed that in the SVN and I get ```
wynneth@wilykat:~$ lyricsdownloaderSVN  -v
Found player: amarokapp
no such function
no such function
Artist: Darude
        Songname: Calm Before The Storm

Lyrics file already exist for: darude  :  calm before the storm
```
So now we're working but I still get the no such function before everything.

I think I've fixed that in the latest svn version. Could you give it a shot? You might have to remove 'amarok' from the list of players again, but I think that just changing the order of detection will work.

---

### Post by wynneth on 2009-02-21
Ah-ha! Didn't have to change a thing in rc29 - worked right out of the box. Naturally, since I was now googling 'reasons to switch to amarok 2 in ubuntu gnome' OR 'differences amarok 2 amarok 1'. LOL
Thanks very much!

---

### Post by eightmillion on 2009-02-21
Thank you for helping me work out those bugs. I don't have amarok 1.x on my system, so it's a big help when someone can try out changes and report the results. :)

---

### Post by wynneth on 2009-02-21
Also, nice roflcopter. I didn't realize there was a voice synth already on my system, which is great since my 5 year old just asked about one earlier. A quick question, and this is really not just about your script but conky scripts in general. Content generated from execs - I can color it, I can font it, but I can only align the first line of output. Is there something I'm missing or does this have to be done in the script itself to work properly? In this case, I'd like to try out alignc and alignr on my lyrics to find a good place on screen for it. If I do ```
 $alignc${exec lyricsdownloader | fold -sw60}
``` The first line is centered, but nothing beyond that. If it's not a possibility, no problem great work anyway! 
As for amarok 1.x, I'm using 1.4 for future reference. I might consider going to 2 at some point but I'm straight Ubuntu 8.1 with Gnome and the only things I've read about it on Gnome mentioned some theming problems. Also, no one mentions if the mini player view is still a part of it.

---

### Post by eightmillion on 2009-02-21
> **wynneth said:**
> Also, nice roflcopter. I didn't realize there was a voice synth already on my system, which is great since my 5 year old just asked about one earlier. A quick question, and this is really not just about your script but conky scripts in general. Content generated from execs - I can color it, I can font it, but I can only align the first line of output. Is there something I'm missing or does this have to be done in the script itself to work properly? In this case, I'd like to try out alignc and alignr on my lyrics to find a good place on screen for it. If I do ```
 $alignc${exec lyricsdownloader | fold -sw60}
``` The first line is centered, but nothing beyond that. If it's not a possibility, no problem great work anyway! 
As for amarok 1.x, I'm using 1.4 for future reference. I might consider going to 2 at some point but I'm straight Ubuntu 8.1 with Gnome and the only things I've read about it on Gnome mentioned some theming problems. Also, no one mentions if the mini player view is still a part of it.

Espeak is tons of fun. As far as the alignment goes, that is something that has to be done in the script as far as I can tell. It shouldn't be very much work to add an option to do that. I'll have to work on that.

Edit: I've added experimental support for what you want to do. In the attached version, there is an option -a or --align that allows you to specify a string to preceed every line of output, so you can use something like: lyricsdownloader -a '${alignr}'

Note that you have to use single quotes around it or bash will think you're trying to pass a variable to the script and it won't work.

---

### Post by wynneth on 2009-03-07
I'm having a new issue and I'm curious whether it's your script or not. Some of the lyrics now are not simply displaying one version of the lyrics that get pulled, but a version, the closing tag </lyrics> and then another full set, sometimes many more. Can the script solve this problem or is it bigger than that?

---

### Post by eightmillion on 2009-03-07
> **wynneth said:**
> I'm having a new issue and I'm curious whether it's your script or not. Some of the lyrics now are not simply displaying one version of the lyrics that get pulled, but a version, the closing tag </lyrics> and then another full set, sometimes many more. Can the script solve this problem or is it bigger than that?

I don't know what would cause that. You might check to see if the version of the lyrics being returned from lyricswiki is like that. Run the command:
```
lyricsdownloader -o ~
```
to save the lyrics to your home directory. Then, open the file in a text editor and see what it looks like.

---

### Post by wynneth on 2009-03-07
Yup, it sure is. I get a version of the lyrics, then the closing tag, version label, and next tag, then another version. Like this: ```
blah blah blah lyrics here
</lyrics>

=Version A=
<lyrics>blah blah blah second version of lyrics here</lyrics>

=Version B=
<lyrics>blah blah blah third version here
```
So basically it's returning the entire page from lyrics wiki and the page happens to have several versions of the song. It may be helpful to note that the first version returned is the album version, which is the one we would pretty much always want anyway, and is labeled as such.

---

### Post by eightmillion on 2009-03-07
> **wynneth said:**
> Yup, it sure is. I get a version of the lyrics, then the closing tag, version label, and next tag, then another version. Like this: ```
blah blah blah lyrics here
</lyrics>

=Version A=
<lyrics>blah blah blah second version of lyrics here</lyrics>

=Version B=
<lyrics>blah blah blah third version here
```
So basically it's returning the entire page from lyrics wiki and the page happens to have several versions of the song. It may be helpful to note that the first version returned is the album version, which is the one we would pretty much always want anyway, and is labeled as such.

I should be able to do something about that. In the mean time, whenever you encounter a song like that, you should be able to go into ~/.lyrics/artistname/ and edit the lyric file corresponding to the song.

---

