---
title: "New App: SopCast Player for Ubuntu"
date: 2009-01-06
forum: Desktop Environments
---

### Post by flyguy97 on 2009-01-06
Hello all,

I created a new SopCast front-end and would love it if people would help test it out a bit. It features a built-in player and a channel guide with the ability to bookmark favorite channels. Currently the only available language is English, but I'm working with a few people to try and bring support for Japanese and Chinese as well. Let me know what needs improvement, and please, be honest.

[http://code.google.com/p/sopcast-player]("http://code.google.com/p/sopcast-player")

btw. Be sure to read the Installation notes on the website before you install, due to the GPL I am unable to include the SopCast client program in the package.

flyguy97

---

### Post by dafoo21 on 2009-01-06
Works great for me! Thats really good timing to post this too!

---

### Post by flyguy97 on 2009-01-06
> **dafoo21 said:**
> Works great for me! Thats really good timing to post this too!

I'm glad it installed ok. Any feedback about the player?

---

### Post by ranjandatta on 2009-01-06
On Jaunty i get this error
```

The program 'sopcast-player.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 7552 error_code 170 request_code 152 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
ranjan@media-workhorse:~$ python: ../../src/xcb_io.c:182: process_responses: Assertion `((int) (((dpy->last_request_read)) - ((dpy->request))) <= 0)' failed.

```
Running it with --sync
```

Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 744, in on_channel_treeview_row_activated
    self.parent.play_channel(self.selection[9], self.selection[1])
  File "/usr/bin/sopcast-player.py", line 394, in play_channel
    self.fork_sop.fork_sop(self.channel_url, str(self.inbound_port), str(self.outbound_port))
  File "/usr/share/sopcast-player/lib/fork.py", line 42, in fork_sop
    os.execlp("sp-sc", "sp-sc", self.sop_address, self.inbound_port, self.outbound_port)
  File "/usr/lib/python2.5/os.py", line 337, in execlp
    execvp(file, args)
  File "/usr/lib/python2.5/os.py", line 354, in execvp
    _execvpe(file, args)
  File "/usr/lib/python2.5/os.py", line 390, in _execvpe
    func(fullname, *argrest)
OSError: [Errno 2] No such file or directory
sopcast-player.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
sopcast-player.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```

---

### Post by flyguy97 on 2009-01-06
[COLOR="Red"]***Update***[/COLOR] I was able to reproduce the bug in Intrepid. A fix has been found and will be incorporated into the next release which will hopefully be out by Jan 12.

Thank you for your reply, I will look into this. I believe it is a problem with the way I fork my process. I will post an updated binary this weekend if I am able to track it down by then. Does this affect playback? Did it terminate the program? What were you doing when the error showed up? An issue has been logged on my project page. Progress of this and all bugs can be monitored at the project issues page [http://code.google.com/p/sopcast-player/issues/list]("http://code.google.com/p/sopcast-player/issues/list"). Thank you again for you post.

Jason

> **ranjandatta said:**
> On Jaunty i get this error
```

The program 'sopcast-player.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 7552 error_code 170 request_code 152 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
ranjan@media-workhorse:~$ python: ../../src/xcb_io.c:182: process_responses: Assertion `((int) (((dpy->last_request_read)) - ((dpy->request))) <= 0)' failed.

```
Running it with --sync
```

Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 744, in on_channel_treeview_row_activated
    self.parent.play_channel(self.selection[9], self.selection[1])
  File "/usr/bin/sopcast-player.py", line 394, in play_channel
    self.fork_sop.fork_sop(self.channel_url, str(self.inbound_port), str(self.outbound_port))
  File "/usr/share/sopcast-player/lib/fork.py", line 42, in fork_sop
    os.execlp("sp-sc", "sp-sc", self.sop_address, self.inbound_port, self.outbound_port)
  File "/usr/lib/python2.5/os.py", line 337, in execlp
    execvp(file, args)
  File "/usr/lib/python2.5/os.py", line 354, in execvp
    _execvpe(file, args)
  File "/usr/lib/python2.5/os.py", line 390, in _execvpe
    func(fullname, *argrest)
OSError: [Errno 2] No such file or directory
sopcast-player.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
sopcast-player.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```

---

### Post by pt123 on 2009-01-07
the problem with the old sopcast player for linux was that you couldn't enter a sopcast URL into it, can this let you do that?

---

### Post by flyguy97 on 2009-01-07
Yes, just enter into the channel bar at the bottom and hit enter or press play. Make sure just to enter the channel address, no port information or anything like that. Also be sure to checkout the bookmark feature, saves from having to remember the sop address.

Jason

> **pt123 said:**
> the problem with the old sopcast player for linux was that you couldn't enter a sopcast URL into it, can this let you do that?

---

### Post by 16777216 on 2009-01-07
```
Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 39, in <module>
    import vlc
ImportError: libvlc.so.0: cannot open shared object file: No such file or directory
```

I have VLC 0.9.4 Grishenko according to VLC's about or, 0.9.4-1ubuntu3 according to synaptic.
I am running Intrepid

---

### Post by hotweiss on 2009-01-07
Works perfectly. Thanks.

PS-Is there website that lists other channels?

---

### Post by jjgomera on 2009-01-07
great :P

Im trying to install deb from google.code, y use hardy and "dependency is not satisfaciable" 
in hardy there is 0.8.6, in deb: >=0.9.4

If i try to remake deb, i can install but:

```
jjgomera@ordenata:~$ sopcast-player.py 
Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 39, in <module>
    import vlc
ImportError: libvlc.so.2: no se puede abrír el archivo de objeto compartido: No existe el fichero ó directorio

jjgomera@ordenata:~$ sudo ln -s /usr/lib/libvlc.so.0.0.0 /usr/lib/libvlc.so.2

jjgomera@ordenata:~$ sopcast-player.py 
Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 39, in <module>
    import vlc
ImportError: /usr/share/sopcast-player/lib/vlc.so: undefined symbol: libvlc_media_player_has_vout

```

or really is necesary this vlc version?

---

### Post by flyguy97 on 2009-01-07
I have not tested this under Hardy, I plan to set aside some time this coming week to hammer out the dependencies. If you would like to still give it a try and don't want to wait until the next release you can install vlc 0.9.x by following the directions [here]("http://ubuntuforums.org/showthread.php?t=986781").

Jason

> **jjgomera said:**
> great :P

Im trying to install deb from google.code, y use hardy and "dependency is not satisfaciable" 
in hardy there is 0.8.6, in deb: >=0.9.4

If i try to remake deb, i can install but:

```
jjgomera@ordenata:~$ sopcast-player.py 
Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 39, in <module>
    import vlc
ImportError: libvlc.so.2: no se puede abrír el archivo de objeto compartido: No existe el fichero ó directorio

jjgomera@ordenata:~$ sudo ln -s /usr/lib/libvlc.so.0.0.0 /usr/lib/libvlc.so.2

jjgomera@ordenata:~$ sopcast-player.py 
Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 39, in <module>
    import vlc
ImportError: /usr/share/sopcast-player/lib/vlc.so: undefined symbol: libvlc_media_player_has_vout

```

or really is necesary this vlc version?

---

### Post by flyguy97 on 2009-01-07
I'm glad that it worked for you, I don't know of any other channel lists. If anyone else does please feel free to share.

> **hotweiss said:**
> Works perfectly. Thanks.

PS-Is there website that lists other channels?

---

### Post by jjgomera on 2009-01-07
> **flyguy97 said:**
> I have not tested this under Hardy, I plan to set aside some time this coming week to hammer out the dependencies. If you would like to still give it a try and don't want to wait until the next release you can install vlc 0.9.x by following the directions [here]("http://ubuntuforums.org/showthread.php?t=986781").

Jason
thanks

i didnt know that really vlc 0.8x and 0.9x are totally different program
Now it work like a champ :D

---

### Post by flyguy97 on 2009-01-07
Just to clarify the difference, python 0.9.x in Ubuntu included the ability to link off libvlc with python bindings. Apparently it was available in 0.8.x, but the Ubuntu packagers decided not to include python support. Python support had to be explicitly requested during the configure stage of building VLC. I hope that makes sense.

> **jjgomera said:**
> thanks

i didnt know that really vlc 0.8x and 0.9x are totally different program
Now it work like a champ :D

---

### Post by mocha on 2009-01-08
This is really nice!  Can you add a function to record the stream?  I'm sure this can be done in VLC.  Thanks!

---

### Post by flyguy97 on 2009-01-08
That is really high on the to do list. Please stay tuned.

> **mocha said:**
> This is really nice!  Can you add a function to record the stream?  I'm sure this can be done in VLC.  Thanks!

---

### Post by tim183 on 2009-01-08
the program installs and opens ok, however when i try to play a channel the program crashes and exits.

I'm running ubuntu intrepid 32 bit fully updated and with vlc v.0.9.4

---

### Post by flyguy97 on 2009-01-08
Did you install the sopcast client software? If not you can find the instructions on the [SopCast Player]("http://code.google.com/p/sopcast-player/wiki/Installation") project page. If you already had the SopCast client software installed please post any error messages returned after the crash by runnint sopcast-player from the command line.

> **tim183 said:**
> the program installs and opens ok, however when i try to play a channel the program crashes and exits.

I'm running ubuntu intrepid 32 bit fully updated and with vlc v.0.9.4

---

### Post by tim183 on 2009-01-08
here is the output when I run he program from terminal and try to open the cctv-5 channel.

tim@tim:~$ /usr/bin/sopcast-player.py
Instanciating mediacontrol
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 751, in on_toolbar_play_clicked
    self.parent.play_channel(self.selection[9], self.selection[1])
  File "/usr/bin/sopcast-player.py", line 394, in play_channel
    self.fork_sop.fork_sop(self.channel_url, str(self.inbound_port), str(self.outbound_port))
  File "/usr/share/sopcast-player/lib/fork.py", line 42, in fork_sop
    os.execlp("sp-sc", "sp-sc", self.sop_address, self.inbound_port, self.outbound_port)
  File "/usr/lib/python2.5/os.py", line 337, in execlp
    execvp(file, args)
  File "/usr/lib/python2.5/os.py", line 354, in execvp
    _execvpe(file, args)
  File "/usr/lib/python2.5/os.py", line 390, in _execvpe
    func(fullname, *argrest)
OSError: [Errno 13] Permission denied
The program 'sopcast-player.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 3701 error_code 14 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
tim@tim:~$ python: ../../src/xcb_io.c:182: process_responses: Assertion `((int) (((dpy->last_request_read)) - ((dpy->request))) <= 0)' failed.

---

### Post by tombott on 2009-01-08
Just in case you missed my post in the other thread flyguy97 

[http://ubuntuforums.org/showpost.php?p=6509154&postcount=60](http://ubuntuforums.org/showpost.php?p=6509154&postcount=60)

Thanks for all your work.

---

### Post by tim183 on 2009-01-08
does that help at all?

---

### Post by flyguy97 on 2009-01-08
It looks like it may be a permissions problem with sp-sc. Go to a command line and execute the following:

```
$ sudo chmod 755 /usr/bin/sp-sc
```

Please let me know if that clears up the problem for you.

Jason

> **tim183 said:**
> here is the output when I run he program from terminal and try to open the cctv-5 channel.

tim@tim:~$ /usr/bin/sopcast-player.py
Instanciating mediacontrol
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 751, in on_toolbar_play_clicked
    self.parent.play_channel(self.selection[9], self.selection[1])
  File "/usr/bin/sopcast-player.py", line 394, in play_channel
    self.fork_sop.fork_sop(self.channel_url, str(self.inbound_port), str(self.outbound_port))
  File "/usr/share/sopcast-player/lib/fork.py", line 42, in fork_sop
    os.execlp("sp-sc", "sp-sc", self.sop_address, self.inbound_port, self.outbound_port)
  File "/usr/lib/python2.5/os.py", line 337, in execlp
    execvp(file, args)
  File "/usr/lib/python2.5/os.py", line 354, in execvp
    _execvpe(file, args)
  File "/usr/lib/python2.5/os.py", line 390, in _execvpe
    func(fullname, *argrest)
OSError: [Errno 13] Permission denied
The program 'sopcast-player.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 3701 error_code 14 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
tim@tim:~$ python: ../../src/xcb_io.c:182: process_responses: Assertion `((int) (((dpy->last_request_read)) - ((dpy->request))) <= 0)' failed.

---

### Post by flyguy97 on 2009-01-08
It may be a problem with file permissions. Run the following from the command line:

```
$ sudo chmod 755 /usr/bin/sp-sc
``` 

Please let me know if that works for you.

Jason

> **ranjandatta said:**
> On Jaunty i get this error
```

The program 'sopcast-player.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 7552 error_code 170 request_code 152 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
ranjan@media-workhorse:~$ python: ../../src/xcb_io.c:182: process_responses: Assertion `((int) (((dpy->last_request_read)) - ((dpy->request))) <= 0)' failed.

```
Running it with --sync
```

Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 744, in on_channel_treeview_row_activated
    self.parent.play_channel(self.selection[9], self.selection[1])
  File "/usr/bin/sopcast-player.py", line 394, in play_channel
    self.fork_sop.fork_sop(self.channel_url, str(self.inbound_port), str(self.outbound_port))
  File "/usr/share/sopcast-player/lib/fork.py", line 42, in fork_sop
    os.execlp("sp-sc", "sp-sc", self.sop_address, self.inbound_port, self.outbound_port)
  File "/usr/lib/python2.5/os.py", line 337, in execlp
    execvp(file, args)
  File "/usr/lib/python2.5/os.py", line 354, in execvp
    _execvpe(file, args)
  File "/usr/lib/python2.5/os.py", line 390, in _execvpe
    func(fullname, *argrest)
OSError: [Errno 2] No such file or directory
sopcast-player.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
sopcast-player.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```

---

### Post by martynp on 2009-01-10
Hi,

Installed OK........ all dependencies met...... player runs OK.

However, initially I get the error that the channel list could not be refreshed due to network errors. I started VLC (installed by package manager) and allowed it to access the internet.

The channel list now refreshes but I just get one entry called 'Other' that shows nothing when clicked.

Any pointers as to what is wrong here?

Many Thanks

---

### Post by flyguy97 on 2009-01-10
In the code when the user clicks refresh from within the channel guide [http://www.sopcast.com/gchlxml]("http://www.sopcast.com/gchlxml") is downloaded and parsed to produce the channel guide. This service has been proven to be unreliable. No doubt when you were receiving the "*List Could Not be Refreshed Due to Network Errors*" the service was either down or too slow to be of any use. The problem with the "Other" can not be so easily explained. Can I assume there are no error messages?

> **martynp said:**
> Hi,

Installed OK........ all dependencies met...... player runs OK.

However, initially I get the error that the channel list could not be refreshed due to network errors. I started VLC (installed by package manager) and allowed it to access the internet.

The channel list now refreshes but I just get one entry called 'Other' that shows nothing when clicked.

Any pointers as to what is wrong here?

Many Thanks

---

### Post by martynp on 2009-01-10
Yes, not long after making this post I discovered that it was just an unreliable connection to the server. The 'Other' was just a part loading of the channel list.

Apart from that, this works like a charm.

Many Thanks

---

### Post by flyguy97 on 2009-01-10
Glad to hear everything works as expected.

Jason

> **martynp said:**
> Yes, not long after making this post I discovered that it was just an unreliable connection to the server. The 'Other' was just a part loading of the channel list.

Apart from that, this works like a charm.

Many Thanks

---

### Post by NoVista on 2009-01-10
Running fine on 8.10.

I'd be interested to know what channels users find the most popular.

---

### Post by flyguy97 on 2009-01-10
I now have permission from sopcast.com to redistribute sp-sc from my project page. You can download if from [here]("http://code.google.com/p/sopcast-player/downloads/list"). The only dependency is libstdc++5, which your package manager should be able to resolve for you automatically. For those of you who manually installed sp-sc I suggest you remove it and install the the deb package. Future releases of SopCast Player will require this package, but for the time being sp-sc is an unchecked requirement. 

On a related note, I am in contact with the Free Software Foundation to see if I can distribute sp-sc as part of the sopcast-player package (not a separate package). If anyone has a definitive source stating whether or not a proprietary program may be distributed with a GPL'd program, I would really appreciate it, I would like to make the installation process as painless as possible.

Jason

---

### Post by flyguy97 on 2009-01-10
Has this issue been resolved?

Jason

> **16777216 said:**
> ```
Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 39, in <module>
    import vlc
ImportError: libvlc.so.0: cannot open shared object file: No such file or directory
```

I have VLC 0.9.4 Grishenko according to VLC's about or, 0.9.4-1ubuntu3 according to synaptic.
I am running Intrepid

---

### Post by flyguy97 on 2009-01-11
[COLOR="Red"]New Release![/COLOR] SopCast Player 0.1.1 has been posted on my [project homepage]("http://code.google.com/p/sopcast-player"). As stated in an earlier post, sp-auth is now added as a dependency, sp-auth can be downloaded from the [downloads]("http://code.google.com/p/sopcast-player/downloads/list") section of my project page. If you manually installed sp-sc (sp-auth) you will need to delete it and install the sp-auth package to satisfy the dependency. Also, SopCast Player and sp-auth are now compatible with all debian-based distributions (including debian), not just Ubuntu.

For those of you interested, today I have petitioned with [http://www.myp2p.eu]("http://www.myp2p.eu") to make it part of there website. If you know of any other like services, please let me know so I can contact them as well.

I would like to take a moment to thank you all for making SopCast Player, in my opinion, a success. Through the first week of wide-spread distribution there have been 60 downloads, all of which have been a result of this thread.

---

### Post by flyguy97 on 2009-01-11
[COLOR="Red"]Updated: RPM packages have been posted to the SopCast Player [projec page]("http://code.google.com/p/sopcast-player"). Please disregard rest of message.[/COLOR]

Help! If anyone has experience creating rpm packages for python I would really appreciate their help with re-pacakaging SopCast Player and sp-auth in rpms. I tried to use alien but it strips out the dependencies. Any help with this would be much appreciated.

---

### Post by 16777216 on 2009-01-11
Actually no, I was just about to ask for a bit of help on how to go about fixing this.

---

### Post by flyguy97 on 2009-01-11
Have you installed SopCast Player 0.1.1 available [here]("http://code.google.com/p/sopcast-player")?

> **16777216 said:**
> Actually no, I was just about to ask for a bit of help on how to go about fixing this.

---

### Post by 16777216 on 2009-01-11
I just did that i still get the same error.

---

### Post by flyguy97 on 2009-01-11
I'm almost certain you issue is with vlc. It appears the python bindings are not enabled, this usually is an indicator of a pre-0.9.x version of vlc. You might want to try to re-install vlc.

> **16777216 said:**
> I just did that i still get the same error.

---

### Post by 16777216 on 2009-01-11
I'm going to try a PPA or two that have newer versions of VLC.
If I can/can't track down the problem then I will come back to you with feed back.

EDIT:
I grabbed 0.9.8 from [https://launchpad.net/~dariovezzosi/+archive](https://launchpad.net/~dariovezzosi/+archive) It works now.

---

### Post by flyguy97 on 2009-01-11
I hope everything works out.

> **16777216 said:**
> I'm going to try a PPA or two that have newer versions of VLC.
If I can/can't track down the problem then I will come back to you with feed back.

---

### Post by Vadi on 2009-01-11
Is there a 64bit available?

---

### Post by flyguy97 on 2009-01-11
Unfortunately no, sopcast.com only has binaries for the 32 bit x86 architecture. I will petition my contact within the company to see if there are any plans to support other architectures. Personally, I would really like to see the ARM processor supported. How nice would it be to get SopCast on a Nokia 800/810?

> **Vadi said:**
> Is there a 64bit available?

---

### Post by Vadi on 2009-01-11
Ahh. Good stuff anyway though.

---

### Post by flyguy97 on 2009-01-11
My previous post may be incorrect, a user on the Fedora side said he was able to use the sopcast client software (sp-auth, not SopCast Player) on 64 bit, I will work on compiling for 64 bit and update this thread with my results, sorry for any confusion. On a side note, I may not get to it until the weekend, it all depends on how busy work is. 

> **Vadi said:**
> Is there a 64bit available?

---

### Post by flyguy97 on 2009-01-12
I'm glad everything worked out, were you using a home built version of VLC prior to updating?

> **16777216 said:**
> I'm going to try a PPA or two that have newer versions of VLC.
If I can/can't track down the problem then I will come back to you with feed back.

EDIT:
I grabbed 0.9.8 from [https://launchpad.net/~dariovezzosi/+archive](https://launchpad.net/~dariovezzosi/+archive) It works now.

---

### Post by flyguy97 on 2009-01-14
[COLOR="Red"]SopCast Player 64 bit Version Just Released!![/COLOR]
I posted the x86_64 version of SopCast Player on my [project page]("http://code.google.com/p/sopcast-player"). The 64 bit version of sp-auth needs to be installed prior to installing SopCast Player. Dependencies should be taken care of by your package manager.

---

### Post by 16777216 on 2009-01-14
> **flyguy97 said:**
> I'm glad everything worked out, were you using a home built version of VLC prior to updating?

Honestly, I haven't the foggiest. I have a lot of PPAs turned on so probably.

---

### Post by flyguy97 on 2009-01-14
Besides internationalization and the ability to record, which are currently in development, is there any other feature you would like to see included in SopCast Player?

---

### Post by Vadi on 2009-01-14
Pausing? So you can go on a break while it keeps downloading & buffering.

Edit: I think it would be better if the channel guide was integrated into the sidebar, like totem does. It would mean it's easier to select a channel / browse through them and not have to manage two dialogs.

(or actually, can this functionality be built into totem? It did get a youtube and bbc plugin... having one program does-it-all would be wonderful :))

---

### Post by 16777216 on 2009-01-14
Single window video/guide.

---

### Post by flyguy97 on 2009-01-14
Integrating everything into totem as a plugin was my first thought. However, it was quickly apparent I would run into dependency problems. I might make a go at it now that I am a lot more familiar with this type of programming.

As for your idea of integrating the channel guide into the main window, I will rebuild the ui to give the user the choice of either an all-in-one interface or the way it is currently. I think most power users would prefer an all-in-one interface while newbies, like myself, would prefer separate dialogs, it makes it a little less cluttered.

In order to integrate a pause feature I would need to add recording first. The reason why is the sopcast client has a limited buffer and thus will dump old frames. My idea to implement live pause is to allow sopcast to buffer as normal, then record before bringing up the media player, once a bit of it is recorded begin playing stream dropping data after it is played. If the user presses pause record everything until the user un-pauses. Does anyone see an alternative to this?

> **Vadi said:**
> Pausing? So you can go on a break while it keeps downloading & buffering.

Edit: I think it would be better if the channel guide was integrated into the sidebar, like totem does. It would mean it's easier to select a channel / browse through them and not have to manage two dialogs.

(or actually, can this functionality be built into totem? It did get a youtube and bbc plugin... having one program does-it-all would be wonderful :))

---

### Post by Vadi on 2009-01-14
I'd say it's the other way around actually, the united interface. Gnome's media player can be pointed out as *the* design for novice users. Keep in mind that it also has a "sidebar" button that hides the sidepanel.

But yeah, if you'd get this into totem, that'd be great.

---

### Post by flyguy97 on 2009-01-15
I see your point and agree, a single window must be more accessible otherwise I would find it hard to believe that Gnome Media Player would adopt such a design. But, since we have the tools I will hold it up to the vote and let the community decide. Please vote for the interface of choice in the thread poll above. I am thinking about including an option to do either but if the vote turns out to be lopsided I will adjust accordingly.

> **Vadi said:**
> I'd say it's the other way around actually, the united interface. Gnome's media player can be pointed out as *the* design for novice users. Keep in mind that it also has a "sidebar" button that hides the sidepanel.

But yeah, if you'd get this into totem, that'd be great.

---

### Post by pramsay13 on 2009-01-21
Hi there, I'm fairly new to Ubuntu after my Vista crashed. I'm loving most things but just trying to tweak a few things to get it the way I want it.
I'm onto getting my football on the laptop, and I was trying to get sopcast installed to watch some games.
I went through all the install things okay and I have the player and the channel guide up, but when I click on a channel it keeps saying connecting and retrying channel down the bottom but nothing happens. I've tried a number of channels so not that.
Any suggestions?

---

### Post by Vadi on 2009-01-21
Yeah I experience the same issue with the "Sports test channel group" ones.

---

### Post by flyguy97 on 2009-01-22
When a user selects a channel my program makes an attempt to connect to the selected channel, if a connection cannot be made within 3 seconds (typically plenty of time to connect to a channel) the current attempt is terminated and a new attempt is spawned. This process will repeat itself until a connection is made or the user selects another channel. If you feel the wait time is too little for your computer and internet connection, you can edit the python file at /usr/bin/sopcast-player.py. Change lines 56 and 57 to longer wait times, for example if you wanted to allow for a 10 second wait you would change the above referenced lines to ```
self.wait_before_retry_time = 10 / self.sleep_time
self.wait_before_restart = 10 / self.sleep_time
```

Keep in mind that even though a channel shows up in the channel guide, that does not mean it is functioning. I have no content control over the channel guide as it is generated from [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml), so complaints about non-functioning channels should be reported to sopcast.com.

Version 0.2.0 (soon to be released) will allow a user customised wait time from a configuration dialogue.

> **pramsay13 said:**
> Hi there, I'm fairly new to Ubuntu after my Vista crashed. I'm loving most things but just trying to tweak a few things to get it the way I want it.
I'm onto getting my football on the laptop, and I was trying to get sopcast installed to watch some games.
I went through all the install things okay and I have the player and the channel guide up, but when I click on a channel it keeps saying connecting and retrying channel down the bottom but nothing happens. I've tried a number of channels so not that.
Any suggestions?

---

### Post by srt4play on 2009-01-26
Works great here on Intrepid, thanks!

---

### Post by joanmunoz on 2009-01-28
Perfect! Works ok in my laptop (Compaq 6720s) running under Ubuntu Intrepid.

Thanks and great work!

Joan

---

### Post by chunchengch on 2009-01-29
How can I edit the bookmark list?

---

### Post by jjgomera on 2009-01-29
all that info is in file ~/.pySopCast/pySopCast.db, its a sqlite database, so you can use sqlitebrowser to edit it

---

### Post by chunchengch on 2009-01-29
> **jjgomera said:**
> all that info is in file ~/.pySopCast/pySopCast.db, its a sqlite database, so you can use sqlitebrowser to edit it

Thanks.

Yes, I can edit the bookmark with sqlitebrowser, but it is better, easier and more regular to do this just within the SopCast Player, isn't it?

---

### Post by flyguy97 on 2009-01-30
Full bookmark management is scheduled for 0.3.0. Version 0.2.0, which includes internationalization support, is scheduled for release on 9 Feb. Version 0.3.0 should follow in another 2-3 weeks. Time permiting of course (my primary job is really busy at the present time).

> **chunchengch said:**
> Thanks.

Yes, I can edit the bookmark with sqlitebrowser, but it is better, easier and more regular to do this just within the SopCast Player, isn't it?

---

### Post by parthbakshi on 2009-01-30
I installed Sopcast player after satisfying the dependencies ,when i try to run it i get this error in terminal 


parth@parth-laptop:~$ /usr/bin/sopcast-player.py 
Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 44, in <module>
    locale.setlocale(locale.LC_ALL, loc)
  File "/usr/lib/python2.5/locale.py", line 478, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting


Any idea how to solve it?

---

### Post by flyguy97 on 2009-01-31
Sorry about this, it appears as you may be using Indian. I guess formating dates in Indian is not supported in gettext. Open /usr/bin/sopcast-player.py and comment out the line that reads
```
locale.setlocale(locale.LC_ALL, loc)
```
it should be around line 44. This should fix the error message, if it doesn't please let me know.

> **parthbakshi said:**
> I installed Sopcast player after satisfying the dependencies ,when i try to run it i get this error in terminal 


parth@parth-laptop:~$ /usr/bin/sopcast-player.py 
Traceback (most recent call last):
  File "/usr/bin/sopcast-player.py", line 44, in <module>
    locale.setlocale(locale.LC_ALL, loc)
  File "/usr/lib/python2.5/locale.py", line 478, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting


Any idea how to solve it?

---

### Post by flyguy97 on 2009-02-01
I am in need of some GPL guidance. I am using GPL v2 for SopCast Player and I would like to know if it is ok to distribute sp-auth (which is free, but proprietary) in the same debian package as SopCast Player. I would like to make SopCast Player easier to install but of course I need to follow the tenets of the GPL. Any inputs, specifically examples, would be greatly appreciated.

---

### Post by flyguy97 on 2009-02-01
I got the answer to my problem, according to a volunteer from gnu.org my specific case fits under [this clause]("http://www.fsf.org/licensing/licenses/gpl-faq.html#GPLInProprietarySystem") of the GNU (best summarised in the last paragraph). In essence, since my program does not directly interact with the proprietary software, a term they refer to as at "arms length", I am free to distribute both in a single package as long as the copyright of each is spelled out and the user know their rights when it comes to each program.

> **flyguy97 said:**
> I am in need of some GPL guidance. I am using GPL v2 for SopCast Player and I would like to know if it is ok to distribute sp-auth (which is free, but proprietary) in the same debian package as SopCast Player. I would like to make SopCast Player easier to install but of course I need to follow the tenets of the GPL. Any inputs, specifically examples, would be greatly appreciated.

---

### Post by Vadi on 2009-02-01
That's good to hear.

---

### Post by flyguy97 on 2009-02-05
I am looking for translators for SopCast Player. I have English, Japanese, and Chinese taken care of, if you would like to see SopCast Player in your language feel free to reply to this message. I will be happy to work with first time translators.

---

### Post by jjgomera on 2009-02-05
> **flyguy97 said:**
> I am looking for translators for SopCast Player. I have English, Japanese, and Chinese taken care of, if you would like to see SopCast Player in your language feel free to reply to this message. I will be happy to work with first time translators.
is po file that it has to translate?

---

### Post by Vadi on 2009-02-05
> **flyguy97 said:**
> I am looking for translators for SopCast Player. I have English, Japanese, and Chinese taken care of, if you would like to see SopCast Player in your language feel free to reply to this message. I will be happy to work with first time translators.

Upload the .po to Launchpad, and you'll be good to go.

why: [https://launchpad.net/+tour/translation](https://launchpad.net/+tour/translation)

---

### Post by flyguy97 on 2009-02-06
Thank you for the heads up. I uploaded the .po file, I'm still trying to figure out how to open for translation. I will update when translation is open. Again, thank you for the tip.

Regards,
Jason

> **Vadi said:**
> Upload the .po to Launchpad, and you'll be good to go.

why: [https://launchpad.net/+tour/translation](https://launchpad.net/+tour/translation)

---

### Post by flyguy97 on 2009-02-08
All,

I am attempting to enable translations for SopCast Player in Launchpad. Whenever I click on the translations link it says > This project is not configured to use Launchpad for translations. I enabled the "Translations for this project are done in Launchpad" option in the Change Project Details section, as well as uploaded a po template file. From the looks of the Wiki I followed all necesary steps to enable translation. I am asking for some insight on what I am doing wrong.

Regards,
Jason

---

### Post by Vadi on 2009-02-08
edit: sorry, I think you did it all right, just on the first time need to wait for a review: [https://translations.launchpad.net/sopcast-player/+imports](https://translations.launchpad.net/sopcast-player/+imports)

---

### Post by flyguy97 on 2009-02-08
Has anyone experienced any problems when removing SopCast Player? One of the users on the Fedora side said that SopCast Player wasn't removed when VLC was removed.

---

### Post by flyguy97 on 2009-02-08
In the interest of quality I am delaying the release of version 0.2.0. During final testing a bug was discovered that may freeze the channel guide window during a refresh. While this doesn't pose a serious problem, I believe it is best to hammer out the bug before final release. This bug should be fixed no later than Tuesday night (GMT). I sincerely apologize for any inconvenience. If you are so inclined, the 0.2.0-pre is available from subversion under the Source heading if you don't want to wait for the official release.

Regards,
Jason

---

### Post by Vadi on 2009-02-08
Not a problem at all. I like your developing style :)

---

### Post by flyguy97 on 2009-02-08
Thank you for the help Vadi. Everything is good to go now.

> **Vadi said:**
> edit: sorry, I think you did it all right, just on the first time need to wait for a review: [https://translations.launchpad.net/sopcast-player/+imports](https://translations.launchpad.net/sopcast-player/+imports)

---

### Post by jjgomera on 2009-02-09
I dont know how use launchpad, so Spanish from Spain translation attached ;)

---

### Post by flyguy97 on 2009-02-09
Thank you so much for your translation. However, a few translation strings were added after this version of the file was released. Attached is the most current version of the translation file. Again, I really appreciate your efforts, thank you.

> **jjgomera said:**
> I dont know how use launchpad, so Spanish from Spain translation attached ;)

---

### Post by jjgomera on 2009-02-10
are you sure you attached the last version, i dont see any untranslated entry

---

### Post by Vadi on 2009-02-10
Ok, the delay in importing was because you uploaded a .po files instead of a .pot (a .pot is the template itself). So when you'll be updating the lp translations, upload a .pot.

They imported it now, so anyone can translate: [https://translations.launchpad.net/sopcast-player/trunk/+pots/sopcast-player](https://translations.launchpad.net/sopcast-player/trunk/+pots/sopcast-player)

edit: oh yeah, and when uploading, also upload the existing .po files - so lp knows that you used the translations and marks them as "syncronized".

---

### Post by Vadi on 2009-02-10
I translated 45% of the project just by clicking on already-translated strings that launchpad auto-suggests from other projects that use its translation system. 

Not bad at all :)

---

### Post by flyguy97 on 2009-02-10
Thank you for the clarification. I updloaded the Chinese file, I will upload the rest when they are ready.

Regards,
Jason

> **Vadi said:**
> Ok, the delay in importing was because you uploaded a .po files instead of a .pot (a .pot is the template itself). So when you'll be updating the lp translations, upload a .pot.

They imported it now, so anyone can translate: [https://translations.launchpad.net/sopcast-player/trunk/+pots/sopcast-player](https://translations.launchpad.net/sopcast-player/trunk/+pots/sopcast-player)

edit: oh yeah, and when uploading, also upload the existing .po files - so lp knows that you used the translations and marks them as "syncronized".

---

### Post by flyguy97 on 2009-02-10
I am sorry, I must have tarred the wrong file. Attached is the correct file.

Regards,
Jason

> **jjgomera said:**
> are you sure you attached the last version, i dont see any untranslated entry

---

### Post by flyguy97 on 2009-02-10
Yes, I love the features that Launchpad brings to the table. Great website.

> **Vadi said:**
> I translated 45% of the project just by clicking on already-translated strings that launchpad auto-suggests from other projects that use its translation system. 

Not bad at all :)

---

### Post by jjgomera on 2009-02-10
> **flyguy97 said:**
> I am sorry, I must have tarred the wrong file. Attached is the correct file.

Regards,
Jason
completed :)

---

### Post by flyguy97 on 2009-02-10
Can you please translate the following

Show Toolbar
Bookmark

Clicking show toolbar will display a toolbar in the main player screen. Bookmark as in add bookmark. I will put in the po file. Thank you.

> **jjgomera said:**
> completed :)

---

### Post by flyguy97 on 2009-02-10
How would you like your name to show up in the translation credits?

> **jjgomera said:**
> completed :)

---

### Post by jjgomera on 2009-02-10
> **flyguy97 said:**
> Can you please translate the following

Show Toolbar
Bookmark

Clicking show toolbar will display a toolbar in the main player screen. Bookmark as in add bookmark. I will put in the po file. Thank you.

Show Toolbar: Mostrar barra de herramientas
Bookmark: If it's an action: *Añadir a favoritos*, in spanish dont exist any "bookmark" verb; or if it's a name, simply *Favoritos*

> How would you like your name to show up in the translation credits?jjgomera is good

---

### Post by flyguy97 on 2009-02-10
Thank you for that, it will be included in 0.2.0, which I will begin to package in about an hour.

Regards,
Jason

> **jjgomera said:**
> Show Toolbar: Mostrar barra de herramientas
Bookmark: If it's an action: *Añadir a favoritos*, in spanish dont exist any "bookmark" verb; or if it's a name, simply *Favoritos*

jjgomera is good

---

### Post by redjedi on 2009-02-10
Thank you so much for this, it seems to work perfectly so far.

I tried installing Sopcast manually on my previous install, and it was a nightmare, this was so easy for a noob like me.

look forward to the updates. How easy will it be to install the newer version?

---

### Post by flyguy97 on 2009-02-10
The new player can install over the old. Even if you have problems just remove the old one and then install, but I don't fore see and problems. If you can stay online for the next 2-3 hours it will be posted then.

Regards,
Jason

> **redjedi said:**
> Thank you so much for this, it seems to work perfectly so far.

I tried installing Sopcast manually on my previous install, and it was a nightmare, this was so easy for a noob like me.

look forward to the updates. How easy will it be to install the newer version?

---

### Post by flyguy97 on 2009-02-10
SopCast 0.2.0 is out. However, I don't have time tonight to make deb package. I have every intention of packaging the debs tonight.

Regards,
Jason

---

### Post by mocha on 2009-02-10
Does your new version support recording?  I don't see it listed as a to-do on your google code page.

---

### Post by flyguy97 on 2009-02-11
That will either be next release or the release after.

> **mocha said:**
> Does your new version support recording?  I don't see it listed as a to-do on your google code page.

---

### Post by flyguy97 on 2009-02-11
Attached is the SopCast Player 0.2.0 package. I am unable to post it to google code due to server problems. Please let me know if you run into any difficulties. Don't forget to install the sp-auth package from [http://code.google.com/p/sopcast-player/downloads/list]("http://code.google.com/p/sopcast-player/downloads/list") before installing.

Regards,
Jason

*Edit: Google code is now functioning and thus deb package removed, please go to [http://code.google.com/p/sopcast-player/downloads/list]("http://code.google.com/p/sopcast-player/downloads/list") to download package

---

### Post by flyguy97 on 2009-02-11
All,

I am in desperate need of a German translator for SopCast Player. If you can help please go to [https://translations.launchpad.net/sopcast-player]("https://translations.launchpad.net/sopcast-player") to translate. Thank you.

Regards,
Jason

---

### Post by Vadi on 2009-02-11
64bit .debs?

---

### Post by oyvindm on 2009-02-11
yeah, is there any 64bit.deb coming? I really hope so. After reading through these ten pages of posts I'm really looking forward to trying out your player.


edit:

I added a Norwegian translation while I'm waiting ;)

---

### Post by chunchengch on 2009-02-11
Thanks for the new SopCast Player 0.2.0 package.

I would like to rebuild the deb to include the favor sop channels, so that I don't have to re-input those to bookmarks when I install SopCast Player on other computers. 

The question is how can I add these channels in pySopCast.glade? thanks for reply.

---

### Post by chunchengch on 2009-02-11
I prefer the default sop channel input block in version 0.1.1.

---

### Post by flyguy97 on 2009-02-11
I will try to get that done at launch today, otherwise tonight after work. Just ran out of time last night.

Cheers

> **Vadi said:**
> 64bit .debs?

---

### Post by flyguy97 on 2009-02-11
My advice is to copy the ~/.pySopCast directory to all your other computers' /home/<user> directory. This will bring over all preferences as well.

Cheers

> **chunchengch said:**
> Thanks for the new SopCast Player 0.2.0 package.

I would like to rebuild the deb to include the favor sop channels, so that I don't have to re-input those to bookmarks when I install SopCast Player on other computers. 

The question is how can I add these channels in pySopCast.glade? thanks for reply.

---

### Post by flyguy97 on 2009-02-12
You can expect a 64-bit deb sometime today. How would you like your name displayed in the translation credits?

Cheers

> **oyvindm said:**
> yeah, is there any 64bit.deb coming? I really hope so. After reading through these ten pages of posts I'm really looking forward to trying out your player.


edit:

I added a Norwegian translation while I'm waiting ;)

---

### Post by flyguy97 on 2009-02-12
I will see if it feasible to re-add that feature in the next release (in about two weeks), As it is now you can use shortcut keys to manage the display mode, if you were to type in the channel input block I would need to block those keyboard events from bubbling up to the window. I'm sure there is a solution but I will have to research it.

> **chunchengch said:**
> I prefer the default sop channel input block in version 0.1.1.

---

### Post by chunchengch on 2009-02-12
Here is the sopcast-player.mo for Traditional Chinese.

[ATTACH]103035[/ATTACH]

---

### Post by flyguy97 on 2009-02-12
Thank you so much. I love how everyone has rallied to make this program successful. How would you like your name to show up in the credits?

> **chunchengch said:**
> Here is the sopcast-player.mo for Traditional Chinese.

[ATTACH]103035[/ATTACH]

---

### Post by chunchengch on 2009-02-12
> **flyguy97 said:**
> ...How would you like your name to show up in the credits?

I have sent you a private message.

---

### Post by flyguy97 on 2009-02-12
Has anyone found any bugs in the program?

> **chunchengch said:**
> I have sent you a private message.

---

### Post by flyguy97 on 2009-02-12
chunchengch,

I actually need the po file, it is a GPL requirement. Thank you again.

Regards,
Jason

> **chunchengch said:**
> Here is the sopcast-player.mo for Traditional Chinese.

[ATTACH]103035[/ATTACH]

---

### Post by flyguy97 on 2009-02-12
All,

SopCast Player 0.2.0 64-bit is available for download from the project page [http://code.google.com/p/sopcast-player]("http://code.google.com/p/sopcast-player").

Regards,
Jason

---

### Post by oyvindm on 2009-02-12
Thank you very much. It worked great. 

as for the credits, that's not really necessary, but if it matters I'll send you a pm with my name.

Thanks again!

---

### Post by Vadi on 2009-02-12
Would it be possible to get this listed on the sopcast site as the unofficial player for ubuntu / fedora?

---

### Post by chunchengch on 2009-02-12
> **flyguy97 said:**
> chunchengch,

i actually need the po file, it is a gpl requirement. Thank you again.

Regards,
jason


[attach]103100[/attach]

---

### Post by chunchengch on 2009-02-12
> **flyguy97 said:**
> Has anyone found any bugs in the program?

How can I retrieve it after I uncheck "Show Contorls"?

---

### Post by flyguy97 on 2009-02-12
Ctrl+h, or h should work. However, I realized last night that if I go into fullscreen the Player loses the ability to pick up the keyboard signals. My suggestion is to avoid fullscreen mode if you are going to be hiding your controls for now. I will fix this in the 0.2.1 release, tentatively scheduled for 28 February. I apologize for any inconvenience.

Cheers,
Jason

> **chunchengch said:**
> How can I retrieve it after I uncheck "Show Contorls"?

---

### Post by flyguy97 on 2009-02-12
Funny you should ask, yesterday I contacted sopcast.com about that very subject. They said they would be happy to add SopCast Player to the downloads page. I assume it will happen sometime soon. I will definitely keep everyone updated. Now if I could just get a Linux mag to review the player...

Cheers

> **Vadi said:**
> Would it be possible to get this listed on the sopcast site as the unofficial player for ubuntu / fedora?

---

### Post by flyguy97 on 2009-02-12
Vadi,

I was unable to find how I should credit for your translation in the po file. It looks like I somehow got my name attached to the translation. How would you like your name to show up in the credits?

Jason

---

### Post by flyguy97 on 2009-02-13
All,

I would like to sincerely thank everyone who has helped to make SopCast Player a complete success. I began work on SopCast Player December 22, 2008. The first release was posted January 4, 2009. And now just a little over a month since the first full release SopCast Player has been made the official Linux Player by sopcast.com [http://sopcast.com/download]("http://sopcast.com/download/"). I am truly humbled by SopCast Player's success and owe you all a debt of appreciation. Thank you to all the translators and user's and those that found problems or suggested ways to improve SopCast Player. Without your help this never would have happened. Again, I sincerely thank you and hope you continue to support SopCast Player.

Best Regards,
Jason

---

### Post by Vadi on 2009-02-13
Was going over the translations - just realized that elipsis' are missing from strings that show "in progress" things like "Updating database" or "Downloading *blah*".

---

### Post by Vadi on 2009-02-13
About translation - there is some property you can use, called "about-translators" or something to retrieve the translators names - but I can't find it atm

---

### Post by flyguy97 on 2009-02-13
I will look into it tonight.

Cheers

> **Vadi said:**
> About translation - there is some property you can use, called "about-translators" or something to retrieve the translators names - but I can't find it atm

---

### Post by flyguy97 on 2009-02-13
If anyone has tried the external player option could they please post their experiences. I am curious if this feature was well implemented and user-friendly enough.

Cheers

---

### Post by Vadi on 2009-02-13
definitely not user-friendly enough (part of why I didn't try it).

imho you should query the mimetype db for apps that support the playback, and offer them in a dropdown box.

(no idea how to check what apps support what mime type, but it's definitately doable)

---

### Post by flyguy97 on 2009-02-13
In order to try SopCast Player with external player, type the command to launch the player plus any parameter you want with the exception of the media source into the external player command input box, the media sources is provided by SopCast Player. The default entry will launch mplayer in a scaled box and keep the player on top. I will look into the mimetype db, this looks to be very promising. Thank you for your suggestion.

Cheers

> **Vadi said:**
> definitely not user-friendly enough (part of why I didn't try it).

imho you should query the mimetype db for apps that support the playback, and offer them in a dropdown box.

(no idea how to check what apps support what mime type, but it's definitately doable)

---

### Post by flyguy97 on 2009-02-14
The next version of SopCast Player should implement your suggested method of looking up mimetypes, thank you for your suggestion. The following is a method to lookup the asf mimetype, it will display a list of executables that support the asf mimetype. Just in case your interested:)

```
import gnomevfs

for app in gnomevfs.mime_get_all_applications("video/x-ms-asf"):
        print app[2]
```

Regards,
Jason

> **Vadi said:**
> definitely not user-friendly enough (part of why I didn't try it).

imho you should query the mimetype db for apps that support the playback, and offer them in a dropdown box.

(no idea how to check what apps support what mime type, but it's definitately doable)

---

### Post by Vadi on 2009-02-14
Ahh. Looks good, except isn't gnomevfs going to be depriciated? you should use gvfs instead

I think this is the replacement: [http://library.gnome.org/devel/gio/stable/gio-GContentType.html](http://library.gnome.org/devel/gio/stable/gio-GContentType.html)

and [here]("http://library.gnome.org/devel/references") it says:

> This module is heading towards planned deprecation. It will continue to be supported and API/ABI stable throughout the GNOME 2.x series, but we do not recommend using it in new applications unless you require functionality that has not already been moved elsewhere.

---

### Post by flyguy97 on 2009-02-15
Thank you for the heads up on gnomevfs' impending deprecation. The documentation on gio (gvfs) in python is terrible. I couldn't find a single good example of using gio, specifically gathering app information, in python. I had to use python's dir command to generate my own makeshift documentation (pen and paper scribbles). The following does the same thing as my previous post. 
```
import gio

for app in gio.app_info_get_all_for_type("video/x-ms-asf"):
	print "Name: %s" % app.get_name()
	print "Command: %s" % app.get_executable()
	print ""
``` 

Regards,
Jason

> **Vadi said:**
> Ahh. Looks good, except isn't gnomevfs going to be depriciated? you should use gvfs instead

I think this is the replacement: [http://library.gnome.org/devel/gio/stable/gio-GContentType.html](http://library.gnome.org/devel/gio/stable/gio-GContentType.html)

and [here]("http://library.gnome.org/devel/references") it says:

---

### Post by Vadi on 2009-02-15
You are right about the missing documentation... I have no idea what package is the gio module for python is coming from, and it's not mentioned at all in the pygtk docs (I did find their tutorial though - wow, it is good).

Looking...

---

### Post by Vadi on 2009-02-15
Well, turns out nobody wrote it yet. They recommended to look at the C docs since they are 'closely matching'.

Meanwhile I've filed a report about it to keep them reminded: [http://bugzilla.gnome.org/show_bug.cgi?id=571834](http://bugzilla.gnome.org/show_bug.cgi?id=571834)

---

### Post by flyguy97 on 2009-02-15
I guess in this case the words 'closely matching' are relative. I had a heck of a time figuring out how they implemented in python.

In your opinion do you think gio is a commonly distributed module, or will I have to do some conditional coding to check for its existence?

Cheers

> **Vadi said:**
> Well, turns out nobody wrote it yet. They recommended to look at the C docs since they are 'closely matching'.

Meanwhile I've filed a report about it to keep them reminded: [http://bugzilla.gnome.org/show_bug.cgi?id=571834](http://bugzilla.gnome.org/show_bug.cgi?id=571834)

---

### Post by Vadi on 2009-02-15
Some older distributions might not ship it, so yes check if gio is installed before using. If it's not installed, hmm... well, fallback to gnomevfs.

---

### Post by flyguy97 on 2009-02-15
Agreed, I will do a rolling fallback, if no gio, fallback to gnomevfs, if no gnomevfs and no gio, fallback to current un-user-friendly external command as it now. Do you mind if I send you a mock up of the dialog box before I finalize? I find that I am not the best judge of ease of use.

Cheers

> **Vadi said:**
> Some older distributions might not ship it, so yes check if gio is installed before using. If it's not installed, hmm... well, fallback to gnomevfs.

---

### Post by Vadi on 2009-02-15
Sure thing. Contact info: [https://launchpad.net/~vperetokin](https://launchpad.net/~vperetokin)

---

### Post by flyguy97 on 2009-02-15
Vadi,

Are you still having issues with SopCast Player freezing while it is buffering?

Jason

---

### Post by Vadi on 2009-02-15
Yes, still happens sometimes. Nothing special in the terminal:

> vadi@ubuntu:~$ sopcast-player.py 
Instanciating mediacontrol
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
Inbound Port: 38149
Outbound Port: 49427
Inbound Port: 38149
Outbound Port: 49427
overflow in spectral RLE, ignoring
Inbound Port: 38149
Outbound Port: 49427



---

### Post by flyguy97 on 2009-02-15
Is it related to a specific channel or does it happen with any channel?

> **Vadi said:**
> Yes, still happens sometimes. Nothing special in the terminal:

---

### Post by Vadi on 2009-02-15
I didn't notice a pattern, so I think with any.

---

### Post by flyguy97 on 2009-02-15
One thing I can suggest is using the external player option if you have mplayer installed. If it still freezes with the external player option then the problem is with SopCast Player, if everything works fine, the problem is with VLC.

> **Vadi said:**
> I didn't notice a pattern, so I think with any.

---

### Post by flyguy97 on 2009-02-17
Did you have any luck testing in out?

Cheers

> **Vadi said:**
> I didn't notice a pattern, so I think with any.

---

### Post by flyguy97 on 2009-02-21
All,

Tomorrow at 4:00pm GMT SopCast Player 0.2.1 will be released. This will add additional language support as well as some minor bug fixes. Languages supported will be Catalan, English, German, Italian, Japanese, Norwegian Bokmal, Russian, Simplified Chinese, Spanish, and Traditional Chinese. I would like to thank all the translators that have freely given of their time. 

I am still looking for additional translations, primarily for European and South American languages. If you able to contribute please visit [https://translations.launchpad.net/sopcast-player]("https://translations.launchpad.net/sopcast-player") to add your language. I will be sure to add your name to the translation credits if you would like.

Cheers,
Jason

---

### Post by flyguy97 on 2009-02-22
All,

SopCast Player 0.2.1 has been posted and is available for download at [http://code.google.com/p/sopcast-player]("http://code.google.com/p/sopcast-player"). Also, I have setup a web page that tracks the total number of downloads by version in case anyone is interested. It is available at [http://download-tracker.appspot.com/]("http://download-tracker.appspot.com/"). Thank you to all of you for your support. And a special thank you to the translators and ogetbilo from [Fedora Forums]("http://forums.fedoraforum.org") for his work with the Makefile and spec file, before his work the source code archive was a real mess.

Regards,
Jason

---

### Post by chunchengch on 2009-02-23
I just install SopCast Player 0.2.1 and have some suggestions,

1. I think it will be more convenient to include the sp-sc in the SopCast Player package.

2. The launcher is placed in category /Applications/Networks by default, but I think it is more proper to be placed in /Applications/Multimedia.

3. The path of Icon is not specified in sopcast-player.desktop, so the launcher does not display the icon correctly.

I rebuild the deb for my own usage and would be pleased to attach here for your reference.


[ATTACH]104363[/ATTACH]

---

### Post by Vadi on 2009-02-23
1) he can't legally do that

---

### Post by flyguy97 on 2009-02-23
1. As Vadi stated, I can't legally do that as ap-auth is under a commercial license and this is an open source project.

2. I agree, I plan on making the change in version 0.3.0.

3. I was unaware of this issue. Can anyone else share their experiences with this issue? On both my fresh vmware images I use to create the deb files everything displayed correctly after installing the file. Did you try logging out and logging in again? As far as the path is concerned gnome should be taking care of that under the hood

Thank you for your input and thank you for supporting SopCast Player.

Cheers,
Jason

> **chunchengch said:**
> I just install SopCast Player 0.2.1 and have some suggestions,

1. I think it will be more convenient to include the sp-sc in the SopCast Player package.

2. The launcher is placed in category /Applications/Networks by default, but I think it is more proper to be placed in /Applications/Multimedia.

3. The path of Icon is not specified in sopcast-player.desktop, so the launcher does not display the icon correctly.

I rebuild the deb for my own usage and would be pleased to attach here for your reference.


[ATTACH]104363[/ATTACH]

---

### Post by flyguy97 on 2009-02-23
Vadi,

Any help for the window freezes in 0.2.1?

Jason

---

### Post by Vadi on 2009-02-23
> **chunchengch said:**
> 
3. The path of Icon is not specified in sopcast-player.desktop, so the launcher does not display the icon correctly.

It shouldn't need to, this is standard. In fact hard-coding the path would be bad because distros change the locations.

---

### Post by Vadi on 2009-02-23
> **flyguy97 said:**
> Any help for the window freezes in 0.2.1?

Haven't been watching too much tv, but it wasn't having problems so far.

---

### Post by flyguy97 on 2009-02-23
Can I clear the bug in google code?

> **Vadi said:**
> Haven't been watching too much tv, but it wasn't having problems so far.

---

### Post by Vadi on 2009-02-23
sure

---

### Post by dittohead80 on 2009-03-11
I've got a bit of a problem with my Sopcast player. It was working ok when I first installed it but after a recent update it comes up with an error message when I try to run it: "RuntimeError: Bad magic number in .pyc file". How do i fix that?

---

### Post by anlag on 2009-03-11
Just wanted to say thanks for a great program. Getting SopCast to work on Ubuntu has always been a bit of a pain earlier, but your program just works perfectly straight away.

Was so grateful I went and made you a Swedish translation for it. Only two items I couldn't translate: "QC" and "QS" which I have no idea what they're referring to, but unless they're some clever abbreviations in English I'd assume whatever they mean they could simply be directly copied into the Swedish version.

Cheers again!

---

### Post by jjgomera on 2009-03-12
> **anlag said:**
> Just wanted to say thanks for a great program. Getting SopCast to work on Ubuntu has always been a bit of a pain earlier, but your program just works perfectly straight away.

Was so grateful I went and made you a Swedish translation for it. Only two items I couldn't translate: "QC" and "QS" which I have no idea what they're referring to, but unless they're some clever abbreviations in English I'd assume whatever they mean they could simply be directly copied into the Swedish version.

Cheers again!
from [here]("http://www.sopcast.com/docs/so.html#5.2"):

> 5.2 QS & QC

Two parameters could be used to monitor the quality of a channel. One is the quality of source (QS) and another is the quality of client network (QC).

QS stands for the quality of the channel source. Low QS value means the SopServer does not receive enough channel content, and it will result in the poor quality of all viewers. If you feed the channel with an external media server's stream, and SopServer presents the poor QS, you should check the connection between SopServer and the media server to see whether the connection can transfer the stream data efficiently and integrally.

QC stands for the average buffer level of all viewers. The high QC value means the p2p network is working greatly and every watcher can receive most of the channel content in its buffer. If a channel has a low QC, you can check
1) whether the SopServer have enough bandwidth to support the p2p distribution.
2) whether most peers in p2p network have not good internet access to share the stream data.

On SopServer, when a channel is broadcasting, you can monitor QS in "server status info" area. You can click the blue "quality bar" on WebPlayer or SopPlayer to see the quality of a channel, QC.

but i wouldn't translate, like kbps

---

### Post by flyguy97 on 2009-03-12
> **anlag said:**
> Just wanted to say thanks for a great program. Getting SopCast to work on Ubuntu has always been a bit of a pain earlier, but your program just works perfectly straight away.

Was so grateful I went and made you a Swedish translation for it. Only two items I couldn't translate: "QC" and "QS" which I have no idea what they're referring to, but unless they're some clever abbreviations in English I'd assume whatever they mean they could simply be directly copied into the Swedish version.

Cheers again!

I can see your question about translation was answered. I just wanted to say thank you for supporting SopCast Player. Your translation has been added to source and will be released as part of the distro packages in the 0.2.2 release which is due out this weekend. Thank you again, and keep up the great work!

Cheers,
Jason

---

### Post by NoelJB on 2009-03-13
> **dittohead80 said:**
> I've got a bit of a problem with my Sopcast player. It was working ok when I first installed it but after a recent update it comes up with an error message when I try to run it: "RuntimeError: Bad magic number in .pyc file". How do i fix that?

I saw the same problem since python was updated in Jaunty.  Because when Python compiles, it embeds its magic number in the resulting .pyc, so when that is loaded against another version of python, things go boom.

To fix the problem, go to /usr/share/sopcast-player/lib/ and delete all of the .pyc files.  But there is a direct reference to .pyc in the launcher, so you must also go to /usr/bin/sopcast-player, and change .pyc to .py.  After that, it should run for you.

---

### Post by NoelJB on 2009-03-13
> **NoelJB said:**
> After that, it should run for you.

Loosely speaking, mind you. Under Jaunty, the channel guide is throwing an exception when you load:

> You must not use 8-bit bytestrings unless you use a text_factory that can interpret 8-bit bytestrings (like text_factory = str). It is highly recommended that you instead just switch your application to Unicode strings.

That does not happen under Intrepid (python 2.5.2).

---

### Post by flyguy97 on 2009-03-13
> **NoelJB said:**
> Loosely speaking, mind you. Under Jaunty, the channel guide is throwing an exception when you load:



That does not happen under Intrepid (python 2.5.2).

What version of Python are you running?

---

### Post by Vadi on 2009-03-13
Jaunty has 2.6

---

### Post by flyguy97 on 2009-03-13
> **Vadi said:**
> Jaunty has 2.6

I am downloading Jaunty right now and will release a new package tomorrow fixing this issue.

Cheers

---

### Post by calin_ionut on 2009-03-17
I installed the sopcast player from source but when i refresh the "SopCast Player Channel Guide" button it doesn`t appear any channel. It download in my home directory the xml file channel_guide.xml in .pySopCast directory but it doesn`t appear in the list. 

Maybe i did something wrong, but if i open a sop address manually it works.

btw... i am using opensuse 11.1 and python 2.6

Cheers!

---

### Post by flyguy97 on 2009-03-18
> **calin_ionut said:**
> I installed the sopcast player from source but when i refresh the "SopCast Player Channel Guide" button it doesn`t appear any channel. It download in my home directory the xml file channel_guide.xml in .pySopCast directory but it doesn`t appear in the list. 

Maybe i did something wrong, but if i open a sop address manually it works.

btw... i am using opensuse 11.1 and python 2.6

Cheers!

There is a known issue with using python 2.6. I am working on a fix for it but I am unsure how long it will take to publish. A workaround is to invoke the executable with the python2.5 command. I will publish a fix as soon as I can find a viable solution.

Cheers,
Jason

---

### Post by NoelJB on 2009-03-19
> **flyguy97 said:**
> There is a known issue with using python 2.6.
[...]
A workaround is to invoke the executable with the python2.5 command.

Yes, just change /usr/bin/sopcast-player as follows:
```

#!/bin/sh
/usr/bin/python**[COLOR="Blue"]2.5[/COLOR]** /usr/share/sopcast-player/lib/sopcast-player.py $@

```

---

### Post by luk1don on 2009-03-25
I'm using Jaunty and I don't see channels list... Any solution?

> You must not use 8-bit bytestrings unless you use a text_factory that can interpret 8-bit bytestrings (like text_factory = str). It is highly recommended that you instead just switch your application to Unicode strings.

---

### Post by dittohead80 on 2009-04-08
> **NoelJB said:**
> Yes, just change /usr/bin/sopcast-player as follows:
```

#!/bin/sh
/usr/bin/python**[COLOR="Blue"]2.5[/COLOR]** /usr/share/sopcast-player/lib/sopcast-player.py $@

```
That worked a treat! Thank you very much :)

---

### Post by stanca on 2009-04-23
Me too,thank you!

---

### Post by MarzioDance on 2009-04-28
Works now, thank you

---

### Post by tilleternity on 2009-04-28
> **flyguy97 said:**
> Yes, just enter into the channel bar at the bottom and hit enter or press play. Make sure just to enter the channel address, no port information or anything like that. Also be sure to checkout the bookmark feature, saves from having to remember the sop address.

Jason

I am running it on jaunty with the python 2.5 as shown in previous posts. I cannot see the channel bar where I can enter the channel number.

---

### Post by sombrancelha on 2009-04-29
Hello,

I installed SopCast Player with no error messages, but when I try to launch it, nothing happens.

I'm running Jaunty. Any idea what might be the problem?

Thanks!

---

### Post by Rofko on 2009-05-02
There is def a bug with this prgram in Jaunty. I have the same problem as sombrancelha. The program simply does not run. If you run it in the terminal, you get the error message:

> RuntimeError: Bad magic number in .pyc file


---

### Post by Operan on 2009-05-05
> **sombrancelha said:**
> Hello,

I installed SopCast Player with no error messages, but when I try to launch it, nothing happens.

I'm running Jaunty. Any idea what might be the problem?

Thanks!

The same to me! :confused:

---

### Post by zeltak on 2009-05-10
same here (RuntimeError: Bad magic number in .pyc file)

Zeltak

---

### Post by todorkichukov on 2009-05-14
> I installed SopCast Player with no error messages, but when I try to launch it, nothing happens. 
You will see **"RuntimeError: Bad magic number in .pyc file"** message only when you run it from terminal. 

This worked great for me, give it a try:
> To fix the problem, go to /usr/share/sopcast-player/lib/ and delete all of the .pyc files. But there is a direct reference to .pyc in the launcher, so you must also go to /usr/bin/sopcast-player, and change .pyc to .py. After that, it should run for you.

---

### Post by marwin82 on 2009-05-15
hey thanks to the author of this application...now sopcast works very good on my jaunty (installing python 2.5 and deleting .pyc)

There is only one issue:
anyone of you have the solutions to open sop-links (like the ones from myp2p/rojadirecta)?

before with another version of gsopcast there were a script (usually called sopper) and some firefox commands to change...i'm trying to find something for this version...anyone can help?

---

### Post by marwin82 on 2009-05-15
the script which i was talking in my previous post is that:

open a new file and copy:
> #!/bin/sh
/usr/bin/sp-sc $1 3908 8908 > /dev/null &
sleep 15
mplayer [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf)
echo Exiting...
kill -9 $(pidof sp-sc)
call the file "sopper"

after
> 
chmod +x sopper
after
> 
sudo mv sopper /usr/bin
finally the firefox instructions:
go to about:config (in the browser address bar)

-right click > New > Boolean
-write: network.protocol-handler.external.sop
-set to: true

-right click > New > String
-write: network.protocol-handler.app.sop
-write: (/usr/bin/sopper)

is possible to make something like that for this version of sopcast?

---

### Post by sombrancelha on 2009-05-15
> **todorkichukov said:**
> > I installed SopCast Player with no error messages, but when I try to launch it, nothing happens. 
You will see **"RuntimeError: Bad magic number in .pyc file"** message only when you run it from terminal. 

This worked great for me, give it a try:
[quote]
To fix the problem, go to /usr/share/sopcast-player/lib/ and delete all of the .pyc files. But there is a direct reference to .pyc in the launcher, so you must also go to /usr/bin/sopcast-player, and change .pyc to .py. After that, it should run for you. [/QUOTE]

thanks, now i could launch the program. i haven't tried watching any channels yet, though.

---

### Post by flyguy97 on 2009-05-17
All,

Sorry for the long wait for the fixes to the issues created by python 2.6+. I ask that some brave testers download and install the latest source from svn. Instructions to download the latest svn sources can be found at [http://code.google.com/p/sopcast-player/source/checkout]("http://code.google.com/p/sopcast-player/source/checkout"). After downloading the repo, issue the following commands:
```
make all
sudo make install-all
```

This should clear up all existing issues. Please post results on this forum so I know if I should create binaries or if its back to the drawing board. Thank you for your understanding and I look forward to your feedback.

Cheers,
Jason

---

### Post by psychokill3r on 2009-06-02
> **NoelJB said:**
> I saw the same problem since python was updated in Jaunty.  Because when Python compiles, it embeds its magic number in the resulting .pyc, so when that is loaded against another version of python, things go boom.

To fix the problem, go to /usr/share/sopcast-player/lib/ and delete all of the .pyc files.  But there is a direct reference to .pyc in the launcher, so you must also go to /usr/bin/sopcast-player, and change .pyc to .py.  After that, it should run for you.

Thanks 

i installing sopcast-player_0.2.1-1_amd64.deb ,sp-auth_3.0.1_amd64.deb
and vlc
machine phenon X3 8400 4gb ram ubuntu 9.04 64bits 
Solved bad magic number.
but no connection:(
i refresh sopcast player channel guide = server down

You must not use 8-bit bytestrings unless you use a text_factory that can interpret 8-bit bytestrings (like text_factory = str). It is highly recommended that you instead just switch your application to Unicode strings.

any solution ?
Thank you very much.:KS

Posted by NoelJB  View Post
Yes, just change /usr/bin/sopcast-player as follows:
Code:

#!/bin/sh
/usr/bin/python2.5 /usr/share/sopcast-player/lib/sopcast-player.py $@

Solved 
Thank You very much

---

### Post by flyguy97 on 2009-06-03
I don't know you expierence level with building from source but the subversion repo within google code has a fix for this, it is the pre 0.3.0 release. I hope to package 0.3.0 soon, maybe tonight, I will let you know when it is available.

Cheers,
Jason

> **psychokill3r said:**
> Thanks 

i installing sopcast-player_0.2.1-1_amd64.deb ,sp-auth_3.0.1_amd64.deb
and vlc
machine phenon X3 8400 4gb ram ubuntu 9.04 64bits 
Solved bad magic number.
but no connection:(
i refresh sopcast player channel guide = server down

You must not use 8-bit bytestrings unless you use a text_factory that can interpret 8-bit bytestrings (like text_factory = str). It is highly recommended that you instead just switch your application to Unicode strings.

any solution ?
Thank you very much.:KS

Posted by NoelJB  View Post
Yes, just change /usr/bin/sopcast-player as follows:
Code:

#!/bin/sh
/usr/bin/python2.5 /usr/share/sopcast-player/lib/sopcast-player.py $@

Solved 
Thank You very much

---

### Post by flyguy97 on 2009-06-04
All,

SopCast Player 0.3.0 is now available for download at [http://code.google.com/p/sopcast-player](http://code.google.com/p/sopcast-player). This version fixes both the channel guide issue and the issue that kept SopCast Player from opening. Additional language support has also been added. Note the main menu entry has moved location from Internet to Sound & Video, this is in response to the overwhelming number of users who prefered the new location. I would like to take a moment to apologize for the long delay in releasing this version. Also, thank you to all of those that have posted ideas on how to work around the pyc issue. Thank you for continued support and I hope you enjoy the new SopCast Player.

Cheers,
Jason

---

### Post by 101011010010 on 2009-06-06
[I]Installed and running perfectly on Jaunty 64. Thank you very much.:-D
[/I]

---

### Post by flyguy97 on 2009-06-06
I am pleased to hear that. I ask that anyone that uses an earlier version of Ubuntu report their experiences as well. I'm almost certain everything should work fine with the earlier versions of Ubuntu but I would greatly appreciate community feedback.

Cheers,
Jason

> **101011010010 said:**
> [I]Installed and running perfectly on Jaunty 64. Thank you very much.:-D
[/I]

---

### Post by hibliss on 2009-06-13
Your project has gotten better and better with time, and I just realized that you added the 64 bit deb to your google page.

Working great for me, no real complaints that have not been addressed.

Stream quality is better than gsopcast and the overall program is better than qsopcast. 

Thank you for all your efforts to improve this over time, and especially for making the 64 bit deb and rpm. People like you are what really make the Linux community strong and make it a pleasure to use FOSS.

Now all I need is more popcorn :popcorn:

---

### Post by flyguy97 on 2009-06-14
Thank you for your kind words. I am glad you enjoy SopCast Player. Have some more popcorn on me! :popcorn:

> **hibliss said:**
> Your project has gotten better and better with time, and I just realized that you added the 64 bit deb to your google page.

Working great for me, no real complaints that have not been addressed.

Stream quality is better than gsopcast and the overall program is better than qsopcast. 

Thank you for all your efforts to improve this over time, and especially for making the 64 bit deb and rpm. People like you are what really make the Linux community strong and make it a pleasure to use FOSS.

Now all I need is more popcorn :popcorn:

---

### Post by ztirffritz on 2009-07-07
I was able to install Sopcast finally because VLC released a deb for VLC 1.0.0 today.  I'm using Ubuntu 8.04 x64.  VLC updated with no errors.  I installed sp-auth and the gui from the debs on the sopcast player page ([http://code.google.com/p/sopcast-player/](http://code.google.com/p/sopcast-player/)).  All installed without any errors.  Sopcast player launches, it downloads channels, then it crashes when I try to load anything.  I'm pretty sure that is not how it is supposed ot work.  I've used this at home on my Mythbuntu box with no problems, but I'm guessing that something is not working with the new version of VLC.  Have any suggestions?

---

### Post by flyguy97 on 2009-07-07
> **ztirffritz said:**
> I was able to install Sopcast finally because VLC released a deb for VLC 1.0.0 today.  I'm using Ubuntu 8.04 x64.  VLC updated with no errors.  I installed sp-auth and the gui from the debs on the sopcast player page ([http://code.google.com/p/sopcast-player/](http://code.google.com/p/sopcast-player/)).  All installed without any errors.  Sopcast player launches, it downloads channels, then it crashes when I try to load anything.  I'm pretty sure that is not how it is supposed ot work.  I've used this at home on my Mythbuntu box with no problems, but I'm guessing that something is not working with the new version of VLC.  Have any suggestions?

Please launch from terminal so you can capture any error messages that may appear. Thank you.

Cheers,
Jason

---

### Post by Ulysses on 2009-07-07
Hello

And thankyou to the genius who did this.

It think it was half a dozen mouse clicks to get it running and now I am watching tv on my pc

And, I am greedy for asking this, but I like my sci-fi and I was wondering what other channels this had to offer for free?

RAR

---

### Post by mamamia88 on 2009-07-08
ok it just goes in an endless loop of connecting/retrying channel when copying and pasting link or clicking built in channels any help?

---

### Post by Green_Star on 2009-07-10
Running Ubuntu 8.04, 32bit, vlc 0.9.9a. I can launch sopcast-player, it opens the window, when I try to start any channel it just crashes. Could you please help me to fix this?

> $ sopcast-player 
Instanciating mediacontrol
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1~ppa1~hardy2' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
Inbound Port: 27225
Outbound Port: 31810
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 760, in on_channel_treeview_row_activated
    self.play_channel(self.selection[9], self.selection[1])
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 1249, in play_channel
    self.fork_sop.fork_sop(self.channel_url, str(self.inbound_port), str(self.outbound_port))
  File "/usr/share/sopcast-player/lib/fork.py", line 51, in fork_sop
    os.execlp("sp-sc", "sp-sc", self.sop_address, self.inbound_port, self.outbound_port)
  File "/usr/lib/python2.5/os.py", line 336, in execlp
    execvp(file, args)
  File "/usr/lib/python2.5/os.py", line 353, in execvp
    _execvpe(file, args)
  File "/usr/lib/python2.5/os.py", line 389, in _execvpe
    func(fullname, *argrest)
OSError: [Errno 2] No such file or directory
python: ../../src/xcb_io.c:182: process_responses: Assertion `((int) (((dpy->last_request_read)) - ((dpy->request))) <= 0)' failed.
Aborted
suma@suma-empire:/etc/apt$ python: ../../src/xcb_io.c:182: process_responses: Assertion `((int) (((dpy->last_request_read)) - ((dpy->request))) <= 0)' failed.




---

### Post by flyguy97 on 2009-07-11
> **Green_Star said:**
> Running Ubuntu 8.04, 32bit, vlc 0.9.9a. I can launch sopcast-player, it opens the window, when I try to start any channel it just crashes. Could you please help me to fix this?

Green_Star,

It appears as though you many not have sp-auth installed or the binary is missing. If you installed SopCast Player with the deb install file it should have prompted you that sp-auth was required. If you have since deleted the file or otherwise corrupted the installation, I would suggest that you completely remove sp-auth with synaptic or aptitude and then reinstall. If you installed SopCast Player using source you will need to install sp-auth as well. If you have any questions please don't hesitate to ask. The instructions for installation can be found [here]("http://code.google.com/p/sopcast-player/wiki/Installation") and the installation files are [here]("http://http://code.google.com/p/sopcast-player/downloads/list").

Cheers,
Jason

---

### Post by flyguy97 on 2009-07-11
> **mamamia88 said:**
> ok it just goes in an endless loop of connecting/retrying channel when copying and pasting link or clicking built in channels any help?

Most likely the channel is down. Please try a different channel. If you still have issues please don't hesitate to ask.

Cheers,
Jason

---

### Post by flyguy97 on 2009-07-11
> **Ulysses said:**
> Hello

And thankyou to the genius who did this.

It think it was half a dozen mouse clicks to get it running and now I am watching tv on my pc

And, I am greedy for asking this, but I like my sci-fi and I was wondering what other channels this had to offer for free?

RAR

RAR,

I'm glad you like the program. I have not been able to find any other reliable resource for additional channels. Google is the only alternative but it is very hit or miss.

Cheers,
Jason

---

### Post by note32 on 2009-07-11
it keeps failing to open for me

---

### Post by Green_Star on 2009-07-11
> **flyguy97 said:**
> Green_Star,

It appears as though you many not have sp-auth installed or the binary is missing. If you installed SopCast Player with the deb install file it should have prompted you that sp-auth was required. If you have since deleted the file or .....

You rocks flyguy, some how my sp-auth is missing, I reinstalled it. Thank you. now everything working fine.

---

### Post by flyguy97 on 2009-07-11
> **Green_Star said:**
> You rocks flyguy, some how my sp-auth is missing, I reinstalled it. Thank you. now everything working fine.

Good to hear its working for you, enjoy!

Cheers,
Jason

---

### Post by flyguy97 on 2009-07-11
> **note32 said:**
> it keeps failing to open for me

note32,

Can you be more specific? Please tell me what you are trying to do. Also, please let me know what happens if you try to use it from the command line. Most errors are reported to the console on fail. Run it the following way from the console:

```
$ sopcast-player
```

Cheers,
Jason

---

### Post by flyguy97 on 2009-07-13
All,

I have completed the initial work of rehosting the channel guide on google app engine. You can see the completed work at [http://sopcast-player.appspot.com/gchlxml]("http://sopcast-player.appspot.com/gchlxml"). However, I need help from anyone who is well versed in Google App Engine. One of the design decisions I made regarding the rehost effort was to refresh the channel guide once every 5 minutes from the sopcast.com servers. I was unable to meet my goal of every 5 minutes and now I only update once every 30 minutes due to high CPU usage, every refresh takes up about 1% of my CPU usage allowance. If anyone can take a look at my code and offer advice on how to stream-line CPU usage I would be grateful and, of course, your name will appear in the credits section of SopCast Player. Attached is the complete code for the rehost.

Cheers,
Jason

---

### Post by jose187 on 2009-07-19
Hello!

I need some help

I'm trying to access a sop:// channel through firefox but I'm not having much luck.

I have already done the about:config bit and created the sopper shell.

The browser then asks me if i want to use sopper to open it or crowse for something else.

This is where the problem is.

I try to chose sopper, but it won't let me. I can choose other stuff, click ok, and the window dissapears. But when i try to choose sopper the window is still there even after pressing OK...

Any ideas?

---

### Post by oogmsn on 2009-08-01
Need help here...I managed to install the sopcast player...but I cant seem to get any channel list whenever I click on the refresh...the channel guide URL seems to be indicated as [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)

Also I cant seem to automatically open this sopcast player from firefox links e.g. sop://broker1.sopcast.com:3912/30931
Nothing happens...anyone can help...

---

### Post by oogmsn on 2009-08-02
I've managed to launch the channel manually via terminal by running it something like this
> sopcast-player sop://broker.sopcast.com:3912/6002 8901 8902

I was wondering if there is an easy way to automate this so that whenever I click on a soplink from firefox it can redirect it into this format?

---

### Post by iakov on 2009-08-07
> **oogmsn said:**
> 
Also I cant seem to automatically open this sopcast player from firefox links e.g. sop://broker1.sopcast.com:3912/30931


When you make sure that  Sopcast is functional, close it.
Here's what I did to open sop:// protocol links automatically in Firefox:

[LIST=1]
[*] In Firefox, in the Location bar, type **about:config** and press Enter.
[*] Right-click anywhere in the grid, choose New, then String.
[*] In the **Enter the preference name** prompt, type in **network.protocol-handler.app.sop** and press OK.
[*] In the **Enter string value** prompt, type **sopcast-player** and press OK.
[*]Try to open sop:// link on your favorite website and you will be presented with dialog box where you can search location of sopcast player. Navigate to ~/usr/bin and point to sopcast-player and click OK.
[*]OK out of dialog box and now all sop:// links should open sopcast player automatically.
[/LIST]
Please note that parts 5 and 6 were written from memory so some of the wording might be incorrect but it should be pretty intuitive.

Hope this helps
Iakov.

---

### Post by centos on 2009-08-15
Hello.
I've installed both packages but can't get it to work.
Running from terminal it shows "timed out" after trying to reload channels (I don't see any).
Running from Opera after clicking sop link it's just buffering and nothing happens. Any help will be appreciated.

---

### Post by flyguy97 on 2009-08-15
> **centos said:**
> Hello.
I've installed both packages but can't get it to work.
Running from terminal it shows "timed out" after trying to reload channels (I don't see any).
Running from Opera after clicking sop link it's just buffering and nothing happens. Any help will be appreciated.

centos,

The application is probably functioning fine. The channel server is  over-worked. I am working on a solution that will rehost the channel guide on Google App Engine. The issue with the player saying buffering and not progressing usually indicates an issue with the channel. My best advice is to try a new channel. I hope to complete the rehost of the channel server within the next couple of months. I will keep everyone posted.

Cheers,
Jason

---

### Post by centos on 2009-08-15
Thanks for reply. I've tried several sop links from myp2p.eu, all with the same effect. I suppose that's not good, is it?

---

### Post by flyguy97 on 2009-08-15
> **centos said:**
> Thanks for reply. I've tried several sop links from myp2p.eu, all with the same effect. I suppose that's not good, is it?

Try launching from the terminal, if there is any problem with your setup they will definitely be reported at the terminal on startup.

Jason

---

### Post by urosg3 on 2009-08-19
I have problem installing player. I download sp-auth_3.0.1_i386.deb for my Ubuntu 9.04 and I install deb package.That works fine. Then i cant find menu entry for player anywhere in menu list.
Solution?

---

### Post by centos on 2009-08-19
> **flyguy97 said:**
> Try launching from the terminal, if there is any problem with your setup they will definitely be reported at the terminal on startup.

Jason

I've done nothing, but reloading channels works now. I've also tried two sopcast links from Opera (for more I'll have to wait until evening when more sports are played) and all I've got was reloading channel. In terminal it was "inbound port xxx; outbound port xxx" over and over. I'll try later.

---

### Post by flyguy97 on 2009-08-19
> **urosg3 said:**
> I have problem installing player. I download sp-auth_3.0.1_i386.deb for my Ubuntu 9.04 and I install deb package.That works fine. Then i cant find menu entry for player anywhere in menu list.
Solution?

If you are using gnome use alacarte to see if someone has disabled the sound and video menu. Let me know what you come up with.

Jason

---

### Post by gotunandan on 2009-08-19
Works well for me on Hardy... watching premierleague football right now !

---

### Post by gotunandan on 2009-08-21
Hey could you to put some help on the code.google.com on how to create the .deb package. I am trying my hand at learning packaging and I wanted to have a go at packaging Sopcast :)
Thanks !

---

### Post by flyguy97 on 2009-08-21
> **gotunandan said:**
> Hey could you to put some help on the code.google.com on how to create the .deb package. I am trying my hand at learning packaging and I wanted to have a go at packaging Sopcast :)
Thanks !

I will put together something and post it on google code. I can't give you a timeline for this. I will post a message on this board when I complete it.

Jason

---

### Post by urosg3 on 2009-08-22
> **flyguy97 said:**
> If you are using gnome use alacarte to see if someone has disabled the sound and video menu. Let me know what you come up with.

Jason

Yes, i`m using GNOME. I solved my problem, with help of serbian LoCo forum. They provide  me some qsopcast front-end and that worked fine.
Tnx for help.

---

### Post by flyguy97 on 2009-08-23
All,

Good news, I completed the channel guide rehost. The idea behind rehosting the channel guide was to give the user a better experience when refreshing the channel guide. When the channel guide is pulled from sopcast.com it would fail about half the time leaving users upset that they are unable to get the latest channel guide (one of the most often reported issues of sopcast player). With the rehost, a copy of the channel guide is hosted on google app engine and is update every 5 minutes, if the channel guide is unable to be downloaded from sopcast.com app engine will serve the last known good version of the channel guide. The drawbacks to this service is that the channel guide may go out of date by a few hours, or, in the worse case, a few days. But if app engine was unable to download the channel guide, sopcast player would be unable to as well. At least with the rehost you will always be able to pull something from app engine. The address for the rehost is [http://sopcast-player.appspot.com/gchlxml]("http://sopcast-player.appspot.com/gchlxml"). I will be running load tests on the rehost over the next week, depending on how these tests go I will put out a new update which will change the default channel guide to the app engine rehost. Feel free to use the rehost in SopCast Player, just go to Edit -> Preferences, click on the Channel Guide tab and change the Channel Guide URL to [http://sopcast-player.appspot.com/gchlxml]("http://sopcast-player.appspot.com/gchlxml"). I hope this will vastly improve the user experience.

Cheers,
Jason

---

### Post by ssri on 2009-08-24
Anyone having any problems using sopcast player 0.3.0 ([http://code.google.com/p/sopcast-player/](http://code.google.com/p/sopcast-player/)) with VLC 1.0.1?  The player loads the sop link fine, but nothing else happens.  Furthermore, vlc cannot start up.  VLC 0.9.9a works okay, except it opens an external window rather than one embedded in the viewer like v0.9.4.

---

### Post by flyguy97 on 2009-08-24
> **ssri said:**
> Anyone having any problems using sopcast player 0.3.0 ([http://code.google.com/p/sopcast-player/](http://code.google.com/p/sopcast-player/)) with VLC 1.0.1?  The player loads the sop link fine, but nothing else happens.  Furthermore, vlc cannot start up.  VLC 0.9.9a works okay, except it opens an external window rather than one embedded in the viewer like v0.9.8.

What os are you using?

---

### Post by ssri on 2009-08-24
> **flyguy97 said:**
> What os are you using?

Kubuntu Jaunty
KDE 4.3.0
QT 4.5.2

Everything worked fine with VLC _v0.9.4_ (amended earlier post).  However, VLC v1.0.1 has much better wmv support.

---

### Post by flyguy97 on 2009-08-24
> **ssri said:**
> Kubuntu Jaunty
KDE 4.3.0
QT 4.5.2

Everything worked fine with VLC _v0.9.4_ (amended earlier post).  However, VLC v1.0.1 has much better wmv support.

How did you install v 1.0.1? I'm assuming you didn't get it from the medibuntu repos.

---

### Post by ssri on 2009-08-25
> **flyguy97 said:**
> How did you install v 1.0.1? I'm assuming you didn't get it from the medibuntu repos.

c-korn's ppa via [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by flyguy97 on 2009-08-25
> **ssri said:**
> c-korn's ppa via [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

I think I've been able to replicate the problem. I installed VLC from the repo you pointed out, now when I launch a link all I get is a green screen with no audio or anything else, is this similar to what you are experiencing?

---

### Post by ssri on 2009-08-27
> **flyguy97 said:**
> I think I've been able to replicate the problem. I installed VLC from the repo you pointed out, now when I launch a link all I get is a green screen with no audio or anything else, is this similar to what you are experiencing?

Somewhat similar.  When I launch a link, I get a gray background with no audio even though I see the datastream buffering between 90-100%.  Normally, with lower versions of vlc, I can see the video onscreen (v0.9.4) or I have to launch vlc externally and enter the url (ie. [http://localhost/tv.asf](http://localhost/tv.asf)) in vlc (v0.9.9a).  Unfortunately, I am able to do neither with v1.0.1, let alone run vlc when sopcast is running.

---

### Post by flyguy97 on 2009-08-27
> **ssri said:**
> Somewhat similar.  When I launch a link, I get a gray background with no audio even though I see the datastream buffering between 90-100%.  Normally, with lower versions of vlc, I can see the video onscreen (v0.9.4) or I have to launch vlc externally and enter the url (ie. [http://localhost/tv.asf](http://localhost/tv.asf)) in vlc (v0.9.9a).  Unfortunately, I am able to do neither with v1.0.1, let alone run vlc when sopcast is running.

When you open externally, are you using the functionality that's built into SopCast Player to do that, or are you opening VLC yourself and opening the address manually?

---

### Post by ssri on 2009-08-27
> **flyguy97 said:**
> When you open externally, are you using the functionality that's built into SopCast Player to do that, or are you opening VLC yourself and opening the address manually?

Okay, this is weird.  So, I'm in a new session from a restart, start up sopcast-player in terminal and now I see video in the main player when using vlc v1.0.1 (albeit with another external window titled X11 output).  Must've been something that happened in the previous session.

Back to your question, during the session when vlc v1.0.1 did not work, I downgrade to v0.9.9a and found the url when starting sopcast-player in terminal.  I forgot what was the message, but I believe sopcast-player referred to vlc not starting up or it not being able to call vlc to open a url.  Again, something externally might have happened during the session where sopcast+vlc went awry.

Also, during that aforementioned session, frustrated I enabled the external mplayer option, which worked for a bit until it froze my X-session.  I had to do a hard reset since sysreq+REISUB did not work.. strange...

---

### Post by flyguy97 on 2009-08-27
> **ssri said:**
> Okay, this is weird.  So, I'm in a new session from a restart, start up sopcast-player in terminal and now I see video in the main player when using vlc v1.0.1 (albeit with another external window titled X11 output).  Must've been something that happened in the previous session.

Back to your question, during the session when vlc v1.0.1 did not work, I downgrade to v0.9.9a and found the url when starting sopcast-player in terminal.  I forgot what was the message, but I believe sopcast-player referred to vlc not starting up or it not being able to call vlc to open a url.  Again, something externally might have happened during the session where sopcast+vlc went awry.

Also, during that aforementioned session, frustrated I enabled the external mplayer option, which worked for a bit until it froze my X-session.  I had to do a hard reset since sysreq+REISUB did not work.. strange...

I apologize but I can't follow what you are saying in the second paragraph. I'm not sure what you mean when you say you found the url in the terminal. But I am pretty sure version 1+ is having an issue playing asf streams. I tried to set up playing with an external VLC instance through both SopCast Player and manually. In either case I was unable to see anything except a green screen with no audio. I have a guy that works on the VLC project, I will see if this is something that is known or if I need to post a bug. Again, thank you for your report, I will keep you posted.

---

### Post by bornagainpenguin on 2009-08-27
Anyone seeing the vlc dependency not installable error should do a search for the VLC PPA and update their VLC player, then the SOPcast Player will become installable.

--bornagainpenguin

---

### Post by ssri on 2009-08-27
> **flyguy97 said:**
> I apologize but I can't follow what you are saying in the second paragraph. I'm not sure what you mean when you say you found the url in the terminal. But I am pretty sure version 1+ is having an issue playing asf streams. I tried to set up playing with an external VLC instance through both SopCast Player and manually. In either case I was unable to see anything except a green screen with no audio. I have a guy that works on the VLC project, I will see if this is something that is known or if I need to post a bug. Again, thank you for your report, I will keep you posted.

What I meant is that I ran sopcast via konsole

```
~$sopcast-player
```

For vlc v0.9.9a, when running this command, there will be an output message saying that vlc cannot be opened and the corresponding url for the video stream of sopcast-player is displayed.  Then I open vlc through my gui and copy+paste the url into vlc (media->open network stream).  After doing that, I can see the stream.  If you continue to encounter problems with sopcast and vlc v1.0.1, it would be great if you can submit a bug report.  Thanks for testing vlc v1.0.1! :)

---

### Post by Checcux on 2009-09-19
Hi all,

I have a similar problem playing a lot of channels for sopcast on myp2p.eu.
Channel buffer is up to 100% but i get a grey window and no sound.

Again, i noted that:

Sopcast player works with VLC 1.0.1, but only on some channel (see SS):

[[IMG]http://img185.imageshack.us/img185/9887/immaginepf.th.jpg[/IMG]]("http://img185.imageshack.us/i/immaginepf.jpg/")

Sopcast player does not work with H.264 channels with VLC 1.0.1 (or other players like mplayer, see SS):

[[IMG]http://img245.imageshack.us/img245/7203/immagine2rv.th.jpg[/IMG]]("http://img245.imageshack.us/i/immagine2rv.jpg/")

[[IMG]http://img199.imageshack.us/img199/967/sop1.th.png[/IMG]](http://img199.imageshack.us/i/sop1.png/)

My questions: Is H264 supported on this linux version of sopcast? May the channels linked on myp2p.eu be encoded with H264?

Best regards,

PS: sorry for my bad english ;)

---

### Post by flyguy97 on 2009-09-20
Checcux,

The Sopcast website says the version of the client software for linux is version 3.0.1 which would seem to be incompatible with H.264 since the Windows client, version 3.2.4, added support for H.264. Sorry for the dispappointing answer. I will contact the Sopcast client author and ask if an updated version of the linux client is in the works.

Cheers,
Jason

> **Checcux said:**
> Hi all,

I have a similar problem playing a lot of channels for sopcast on myp2p.eu.
Channel buffer is up to 100% but i get a grey window and no sound.

Again, i noted that:

Sopcast player works with VLC 1.0.1, but only on some channel (see SS):

[[IMG]http://img185.imageshack.us/img185/9887/immaginepf.th.jpg[/IMG]]("http://img185.imageshack.us/i/immaginepf.jpg/")

Sopcast player does not work with H.264 channels with VLC 1.0.1 (or other players like mplayer, see SS):

[[IMG]http://img245.imageshack.us/img245/7203/immagine2rv.th.jpg[/IMG]]("http://img245.imageshack.us/i/immagine2rv.jpg/")

[[IMG]http://img199.imageshack.us/img199/967/sop1.th.png[/IMG]](http://img199.imageshack.us/i/sop1.png/)

My questions: Is H264 supported on this linux version of sopcast? May the channels linked on myp2p.eu be encoded with H264?

Best regards,

PS: sorry for my bad english ;)

---

### Post by Checcux on 2009-09-20
Thanks for your quick reply ;)

Your sopcast player GUI is quite good. I hate to switch on windows... :(

Regards,
Checcux

---

### Post by tzepu on 2009-10-19
i met  a problem trying to install it
i run kubuntu 9.10 beta and there are unmet dependencies that i couldn't solve 
when trying to install sp_auth.... file it requires a library that is obsolete version 5, i already have version 6-4 installed
any advice?

---

### Post by flyguy97 on 2009-10-19
> **tzepu said:**
> i met  a problem trying to install it
i run kubuntu 9.10 beta and there are unmet dependencies that i couldn't solve 
when trying to install sp_auth.... file it requires a library that is obsolete version 5, i already have version 6-4 installed
any advice?

When you installed the 6-4 was it from source or was it part of the standard Ubuntu repos?

---

### Post by ikisham on 2009-10-22
First of all, thank you for this. I haven't installed already but p2p video is really democratic.

I'm installing it on antiX (Debian testing). Already installed sp-auth (had to download libstdc++5 - the system one is libstdc++6 - but all went fine). Now I have the option to install sopcast-player with or without vlc python bindings. I don't know if my VLC has these python bindings. Would it be adverse if I installed with 'install-all' instead of just 'install'?

My VLC is 1.0.2
```
Package: vlc
Priority: optional
Section: video
Installed-Size: 3724
Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 1.0.2-1
Replaces: vlc-nox (<< 0.9.2-1)
Provides: mp3-decoder
Depends: vlc-nox (= 1.0.2-1), libaa1 (>= 1.4p5), libc6 (>= 2.8), libdbus-1-3 (>= 1.0.2), libfreetype6 (>= 2.2.1), libfribidi0 (>= 0.10.9), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.8.0), libnotify1 (>= 0.4.5), libnotify1-gtk2.10, libqtcore4 (>= 4:4.5.2), libqtgui4 (>= 4:4.5.2), libsdl-image1.2 (>= 1.2.5), libsdl1.2debian (>= 1.2.10-1), libstdc++6 (>= 4.2.1), libtar, libvlccore2 (>= 1.0.0~rc1), libx11-6, libxext6, libxinerama1, libxv1, libxxf86vm1, zlib1g (>= 1:1.2.3.3.dfsg), ttf-dejavu-core
Suggests: mozilla-plugin-vlc, videolan-doc
Conflicts: vlc-nox (<< 0.9.2-1)
Filename: pool/main/v/vlc/vlc_1.0.2-1_i386.deb
Size: 1606036
MD5sum: aabbf2b549b4cea2c2cdb7d9ea43eca0
SHA1: 7ed4b4f3aac5d7073408d5ccadd379574be59a25
SHA256: e0bad4e88c64bb2ddba3697370613b372598869b1bfc4631b13205b1749a8408
Description: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
 .
 VLC can also be used as a streaming server that duplicates the stream it
 reads and multicasts them through the network to other clients, or serves
 them through HTTP.
 .
 VLC has support for on-the-fly transcoding of audio and video formats, either
 for broadcasting purposes or for movie format transformations. Support for
 most output methods is provided by this package, but features can be added
 by installing additional audio plugins (vlc-plugin-pulse, vlc-plugin-sdl)
 or video plugins (vlc-plugin-sdl, vlc-plugin-ggi, vlc-plugin-svgalib). There
 is also a web browser plugin in the mozilla-plugin-vlc package.
Homepage: http://www.videolan.org/vlc
Tag: interface::x11, protocol::ipv6, protocol::ssl, role::program, scope::application, sound::compression, sound::player, uitoolkit::ncurses, uitoolkit::wxwidgets, use::converting, use::playing, works-with::audio, works-with::video, works-with-format::{mp3,oggtheora,oggvorbis,wav}

```

Also, just to know, I'm guessing I can open sopcast streams from the command line without sopcast-player (only sp-auth). If it's so, how would I open [http://suprememastertv.com/webtv/sopcast.php](http://suprememastertv.com/webtv/sopcast.php) ?

Regards.

---

### Post by CupofDice on 2009-10-23
Hey guys. I get video, no problem, but not sound. Any ideas? I tried setting vlc to alsa, but that didn't work.

Edit: Sound is now working.

---

### Post by chaopoch on 2009-10-25
I just upgraded Ubuntu 9.04 to 9.10, and the vlc version is 1.0.2, now the Sopcast Player will not integrate the vlc into its interface, how can I solve this problem? thanks.

Here is the screenshot attached for your reference.

[ATTACH]133044[/ATTACH]

---

### Post by joanmunoz on 2009-11-01
> **tzepu said:**
> i met  a problem trying to install it
i run kubuntu 9.10 beta and there are unmet dependencies that i couldn't solve 
when trying to install sp_auth.... file it requires a library that is obsolete version 5, i already have version 6-4 installed
any advice?

Hi!

I have the same problem. I installed that library from standard Ubuntu repos. Any help?

Linux joan-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Thanks!

---

### Post by flyguy97 on 2009-11-01
> **joanmunoz said:**
> Hi!

I have the same problem. I installed that library from Ubuntu sources. Any help?

Linux joan-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Thanks!

All,

Please be patient, I know there are some issues with using SopCast Player with Ubuntu 9.10, I am working on upgrading my distribution to 9.10 as I type this (only 3 more hours until everything is downloaded, BT broadband is well below par). The issues with the dual VLC screens has to do with a change in the Python bindings, shouldn't be hard to resolve. The issue with the C++ library is a little more difficult to pin down, for some reason version 5 of the library has been removed in Karmic, I will see if it simply a matter of changing requirements or if I will have to make a PPA that will house the old library. In any event I am hoping to have a new version of SopCast Player by the end of the week so I can package it during the weekend. As a side note, the change to the Python bindings will mean it is no longer necessary to compile, this could result in merging the two packages (x86 and 64-bit). Sorry for the inconvenience.

Cheers,
Jason

---

### Post by flyguy97 on 2009-11-01
> **flyguy97 said:**
> All,

Please be patient, I know there are some issues with using SopCast Player with Ubuntu 9.10, I am working on upgrading my distribution to 9.10 as I type this (only 3 more hours until everything is downloaded, BT broadband is well below par). The issues with the dual VLC screens has to do with a change in the Python bindings, shouldn't be hard to resolve. The issue with the C++ library is a little more difficult to pin down, for some reason version 5 of the library has been removed in Karmic, I will see if it simply a matter of changing requirements or if I will have to make a PPA that will house the old library. In any event I am hoping to have a new version of SopCast Player by the end of the week so I can package it during the weekend. As a side note, the change to the Python bindings will mean it is no longer necessary to compile, this could result in merging the two packages (x86 and 64-bit). Sorry for the inconvenience.

Cheers,
Jason


All,

The problem with the dual windows has been fixed, now the only video that shows up is at the expected main player. However, there is some difficulties with the sp-sc package. I am not sure why but the libstdc++5 library has been removed from the standard Ubuntu repositories, I will have to create a ppa that will satisfy that requirement. I am not really sure when I will be able to complete this as I have never had to do it before, if anyone would like to create a package for libstdc++5 I would be glad to host it out of my ppa, please let me know.

Cheers,
Jason

---

### Post by flyguy97 on 2009-11-02
> **flyguy97 said:**
> All,

The problem with the dual windows has been fixed, now the only video that shows up is at the expected main player. However, there is some difficulties with the sp-sc package. I am not sure why but the libstdc++5 library has been removed from the standard Ubuntu repositories, I will have to create a ppa that will satisfy that requirement. I am not really sure when I will be able to complete this as I have never had to do it before, if anyone would like to create a package for libstdc++5 I would be glad to host it out of my ppa, please let me know.

Cheers,
Jason

An updated version of SopCast Player is now available through subversion, I will hopefully get to work on packaging sometime this weekend. To get a preview issue the following command to download the source.
```
svn checkout http://sopcast-player.googlecode.com/svn/trunk/ sopcast-player
```

To run it use the following command
```
sopcast-player/lib/sopcast-player.py
```

Please let me know if you have any issues running the preview, if reported in time I will be able to merge a fix before I create the binary packages.

Cheers,
Jason

---

### Post by flyguy97 on 2009-11-02
Attached is a pre-release of SopCast Player 0.3.1, can as many people as possible give it a try to make sure the video issues are sorted out? I would really like it if people using different releases could confirm if it still backwards compatible. Thank you.

Cheers,
Jason

---

### Post by chunchengch on 2009-11-02
> **flyguy97 said:**
> Attached is a pre-release of SopCast Player 0.3.1, can as many people as possible give it a try to make sure the video issues are sorted out?...

The problem with the dual windows is solved, thanks.


> **flyguy97 said:**
> ... I am not sure why but the libstdc++5 library has been removed from the standard Ubuntu repositories, I will have to create a ppa that will satisfy that requirement. I am not really sure when I will be able to complete this as I have never had to do it before, if anyone would like to create a package for libstdc++5 I would be glad to host it out of my ppa, please let me know...

There is a deb available here [http://packages.debian.org/stable/base/libstdc++5](http://packages.debian.org/stable/base/libstdc++5)

---

### Post by joanmunoz on 2009-11-03
Hi!

Video issues solved. Everything fine.

Thanks!

Joan

Linux joan-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by realzippy on 2009-11-03
> **flyguy97 said:**
> Attached is a pre-release of SopCast Player 0.3.1, can as many people as possible give it a try to make sure the video issues are sorted out? I would really like it if people using different releases could confirm if it still backwards compatible. Thank you.

Cheers,
Jason

Will there be a 64bit edition also?

---

### Post by flyguy97 on 2009-11-03
> **realzippy said:**
> Will there be a 64bit edition also?

SopCast Player is now 100% python, it shouldn't make a difference what architecture. Please try it out and let me know.

Cheers,
Jason

---

### Post by realzippy on 2009-11-03
it says "wrong architecture"...

---

### Post by flyguy97 on 2009-11-03
> **realzippy said:**
> it says "wrong architecture"...

I sent you a pm. For all other 64-bit users, I asked realzippy to try an alternative installation procedure, if it works out I will publish the instructions on here and my project home page at google code.

Cheers,
Jason

---

### Post by realzippy on 2009-11-03
Works!!:popcorn:


Means it installs fine,but,unfortunately,cannot reach any sender.

---

### Post by flyguy97 on 2009-11-03
All,

I am pleased to announce I have set-up a PPA that will aid in installation and receiving future updates. Please go to my [PPA]("https://launchpad.net/~jason-scheunemann/+archive/ppa") page on LaunchPad for instructions on how to configure your computer to work with my [PPA]("https://launchpad.net/~jason-scheunemann/+archive/ppa"). Thank you to all of you who tested the pre-release, so far I haven't heard of any issues. 

*NOTE*: If you are a new user of SopCast Player you will need to manually satisfy the sp-auth dependency before installing sopcast-player due to licensing issues (sp-auth is not open source). Please visit [http://code.google.com/p/sopcast-player/downloads/list]("http://code.google.com/p/sopcast-player/downloads/list") to find a package that matches your architecture.

---

### Post by realzippy on 2009-11-03
> **realzippy said:**
> Works!!:popcorn:


Means it installs fine,but,unfortunately,cannot reach any sender.

This was for Karmic 64bit.
Produced this error:

sp-sc: error while loading shared libraries: libstdc++.so.5: cannot open shared object file

[I]tried do set some links,cause libstdc++.so.5 **is** installed,but no luck.
[/I]
**Can anybody confirm/test for Karmic 64 please?!**

So I booted my old Intrepid 64 bit,and **it works** perfectly!:D
I do not have a Jaunty to test,skipped that...

---

### Post by empax on 2009-11-04
Very nice =) I installed x64. for ubuntu 9.04
But i want to wach Turkish TV too. is it possible ?
Thanks.

Edit:
I found. CTRL+O and add link of the channels.:D it's simple sorry.

---

### Post by ian2112 on 2009-11-07
Hello,

I believe I have sopcast installed correctly (9.10) but it keeps trying to conect / retry any channel or link that I try.

I'm not that technically savy so most of my setings would be default.  I was thinking somewhere a port was blocked but my router config is pretty much default.

Anything I could try, or look at that might help troubleshoot?

Much appreciated!
Ian.

---

### Post by flyguy97 on 2009-11-08
> **ian2112 said:**
> Hello,

I believe I have sopcast installed correctly (9.10) but it keeps trying to conect / retry any channel or link that I try.

I'm not that technically savy so most of my setings would be default.  I was thinking somewhere a port was blocked but my router config is pretty much default.

Anything I could try, or look at that might help troubleshoot?

Much appreciated!
Ian.


The good news is everything appears to be installed correctly, (btw did you use the PPA?). Try opening SopCast Player and then going to File -> Open and then enter sop://202.190.75.151:3912/16499 (this channel always seems to work) in the Sop Address field. Let me know how it goes.

Cheers,
Jason

---

### Post by thunderbear on 2009-11-08
hi

i'm using karmic64 with all the updates just tried your sopcast link doesnt work for me

just sits there retrying on karmic64, works fine on my shuttle  running karmic32, so def a 64bit related problem, i'll reinstall and try again...

---

### Post by ian2112 on 2009-11-08
> **flyguy97 said:**
> The good news is everything appears to be installed correctly, (btw did you use the PPA?). Try opening SopCast Player and then going to File -> Open and then enter sop://202.190.75.151:3912/16499 (this channel always seems to work) in the Sop Address field. Let me know how it goes.

Cheers,
Jason

Thanks for the suggestion, Jason.  I tried the address above and experienced the same issue  connecting... retrying...

Yes, I used the PPA.

Any other thoughts or suggestions?  I suspect it's not sopcast but something in between blocking the connection...

Again thanks,
Ian.

---

### Post by ssdt on 2009-11-09
could anyone please give me an update if it works if you click on channels from myp2p.eu and such? i need to see channels from that site.

---

### Post by flyguy97 on 2009-11-09
> **ssdt said:**
> could anyone please give me an update if it works if you click on channels from myp2p.eu and such? i need to see channels from that site.

I haven't added that functionality yet. I have no idea when this will be available, sorry I didn't have better news.

Cheers,
Jason

---

### Post by ssdt on 2009-11-09
can i manually set it up somehow? such as running from the terminal using the program?

---

### Post by flyguy97 on 2009-11-09
> **ssdt said:**
> can i manually set it up somehow? such as running from the terminal using the program?


Yes, you can either do it from the command line, just type the channel address after sopcast-player. Or open SopCast Player then go to File -> Open and then enter the sop address there.

Cheers,
Jason

---

### Post by madone1 on 2009-11-09
> **flyguy97 said:**
> The good news is everything appears to be installed correctly, (btw did you use the PPA?). Try opening SopCast Player and then going to File -> Open and then enter sop://202.190.75.151:3912/16499 (this channel always seems to work) in the Sop Address field. Let me know how it goes.
Cheers,
Jason
I have sopcast installed sopcast-player64 with libstdc++5 integrated and sp-auth in (9.10) but it keeps trying to conect / retry any channel or link that I try. But advised channel works. When channel opens it runs two vlc(XVideo output) screens ??? Way other channels don`t work? 

Thanks

---

### Post by flyguy97 on 2009-11-10
> **madone1 said:**
> I have sopcast installed sopcast-player64 with libstdc++5 integrated and sp-auth in (9.10) but it keeps trying to conect / retry any channel or link that I try. But advised channel works. When channel opens it runs two vlc(XVideo output) screens ??? Way other channels don`t work? 

Thanks

Please follow the instructions at [https://launchpad.net/~jason-scheunemann/+archive/ppa]("https://launchpad.net/~jason-scheunemann/+archive/ppa") to install my ppa, the version available there takes care of the dual video problem. Also, since it is repository, you will always get the latest bug-fixes and enhancements whenever you update your computer. What version of libstdc++5 did you install, if you could write a quick how-to I think that would help a lot of fellow users who are experiencing difficulties getting the 64-bit version working properly.

Cheers,
Jason

---

### Post by joanmunoz on 2009-11-10
> **flyguy97 said:**
> The good news is everything appears to be installed correctly, (btw did you use the PPA?). Try opening SopCast Player and then going to File -> Open and then enter sop://202.190.75.151:3912/16499 (this channel always seems to work) in the Sop Address field. Let me know how it goes.

Cheers,
Jason

Hi Jason,

I have the same issue (Connect/Retry Channel). I've tested the one you suggested with success, but almost every other channel failed. Anyway, I have just added your PPA. Any suggestion?

Thx!

Joan

---

### Post by juliansuddaby on 2009-11-10
After some messing around on my Karmic 64bit, here's what worked for me:

1. Download the modified version of Sopcast-Player (64) from the non-PPA source below. They seem to have added something to fix the libstdc5++ dependency. Sp-sc works via CLI after this sopcast-player64 has been installed

[http://www.sourceslist.eu/installare-software-tramite-repository/installare-sopcast-player-0-3-0-su-ubuntu-karmic-koala-9-10-in-pochi-click/](http://www.sourceslist.eu/installare-software-tramite-repository/installare-sopcast-player-0-3-0-su-ubuntu-karmic-koala-9-10-in-pochi-click/)

2. Using the channel list does not work for me (the constant reloading problem), and neither does using the CLI with a sop address taken from [http://www.sopcast.com/chlist.xml](http://www.sopcast.com/chlist.xml). However, the addresses taken from the Google cache of [http://channel.sopcast.com/channel/](http://channel.sopcast.com/channel/) (which is down for me) seem to work fine in SopCast Player and for the CLI.

NB: Because of not using the PPA version, you get two video windows opening up.

A little bit of a mess right now! But thanks to the author of SopCast Player for making this all possible.

---

### Post by flyguy97 on 2009-11-11
All,

I added a version of libstdc++5 to my ppa which should overcome the issues encountered when using SopCast Player with Ubuntu 9.10, can someone verify this works on the 64-bit platform. To perform the install first be sure you are using my ppa. Directions can be found [here]("https://launchpad.net/~jason-scheunemann/+archive/ppa"). Then perform the following:
```
$ sudo apt-get update
$ sudo apt-get install libstdc++5
```

Note: If it the first time you are installing be sure to grab sp-auth from [here]("http://code.google.com/p/sopcast-player/downloads/list") after installing libstdc++5, then perform the following:
```
$ sudo apt-get install sopcast-player
```

Let me know how it works. If everything goes smoothly I will release a version of SopCast Player that can be completely installed from the PPA with just one command (I know installation is a mess right now), no need to visit the Google Code page. I believe this will add a wider user-base to the program, and hopefully more channels everyone can enjoy.

Cheers,
Jason

---

### Post by juliansuddaby on 2009-11-11
Jason:

Apt-get downloads and installs the libstdc++5 .deb from your PPA fine, but sp-sc still fails with the message:

sp-sc: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Thanks for your quick work on this, though!

---

### Post by flyguy97 on 2009-11-11
> **juliansuddaby said:**
> Jason:

Apt-get downloads and installs the libstdc++5 .deb from your PPA fine, but sp-sc still fails with the message:

sp-sc: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Thanks for your quick work on this, though!

Wow, I am really at a loss for this one. The x86 worked fine on my system, however I don't have a 64-bit system so troubleshooting is real pain. It looks like back to the drawing board.

Cheers,
Jason

---

### Post by flyguy97 on 2009-11-11
> **juliansuddaby said:**
> Jason:

Apt-get downloads and installs the libstdc++5 .deb from your PPA fine, but sp-sc still fails with the message:

sp-sc: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Thanks for your quick work on this, though!

Can you please check if you have ia32-libs installed. This may be the key to all of this.

---

### Post by flyguy97 on 2009-11-11
> **juliansuddaby said:**
> Jason:

Apt-get downloads and installs the libstdc++5 .deb from your PPA fine, but sp-sc still fails with the message:

sp-sc: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Thanks for your quick work on this, though!

Please disregard the previous message, I figured out what I need to fix. Jaunty and previous included libstdc++5 as part of its ia32-libs package. The package included two files:

```
/usr/lib32/libstdc++.so.5
/usr/lib32/libstdc++.so.5.0.7

```

Please try and symlink the files that were part of the libstdc++5 install to the /usr/lib32 directories and let me know if that works. If so, we are probably only a week away from having a ppa that only needs the apt-get install sopcast-player and it will satisfy all its own dependencies automatically.

Cheers,
Jason

---

### Post by serstickman on 2009-11-11
Thanks for all you've done in making this player work.  Greatly appreciate it!

---

### Post by joanmunoz on 2009-11-12
Jason, thanks for all the time and efforts you're putting on this.

Regards!

Joan

---

### Post by embeddeddeveloper on 2009-11-12
> **flyguy97 said:**
> Please disregard the previous message, I figured out what I need to fix. Jaunty and previous included libstdc++5 as part of its ia32-libs package. The package included two files:

```
/usr/lib32/libstdc++.so.5
/usr/lib32/libstdc++.so.5.0.7

```Please try and symlink the files that were part of the libstdc++5 install to the /usr/lib32 directories and let me know if that works. If so, we are probably only a week away from having a ppa that only needs the apt-get install sopcast-player and it will satisfy all its own dependencies automatically.

Cheers,
Jason


Hi Jason, 
Thanks for all your efforts so far. I have had a dickens of a time getting sp-sc to work in 64-bit karmic.

I had the same missing library error as the others and I tried your suggestion of creating the sym links in the /usr/lib32 directory. 

Now I get a different error:
```
owner@owner-laptop:~$ sp-sc
sp-sc: error while loading shared libraries: libstdc++.so.5: wrong ELF class: ELFCLASS64
```As you can see it is perhaps looking for a 32 bit ELF class so linking the 64 bit ones won't work.

I am going to try to hack in the 32bit libs and see what happens.

Chris

---

### Post by flyguy97 on 2009-11-12
All,

I truly appreciate everyone's patience and gratitude regarding the 64-bit version. The good news is, its fixed. I created a package called lib32stdc++5 in my ppa, be sure to do an apt-get update before trying to install. This time I can verify the fix works as I finally went out and purchased a 64-bit machine, I'm sure it will prove to be a worthy investment. I hope that within the next week I can completely repackage SopCast Player so a new user would only have to add my ppa than do an apt-get install sopcast-player for a complete install. Thank you for your patience.

Cheers,
Jason

P.S. I know SopCast Player isn't the only package that suffered from the libstdc++5 issue, please feel free to spread the word about lib32stdc++5, I know a lot of older programs are suffering due to a lack of insight in removing this package from the default repositories.

---

### Post by flyguy97 on 2009-11-13
All,

The good news keeps coming in. I just received an email from the author of the Sopcast client software which contained an updated version of the Linux binary that includes support for H264 channels. I will release this as part of SopCast Player just as soon as I can test it out a bit. If you can't wait to get your hands on it I have attached a copy of the client software. Just make sure that you have a symlink in your /usr/bin directory named sp-sc that points to the actual location of this file.

Cheers,
Jason

---

### Post by mocha on 2009-11-13
> **flyguy97 said:**
> All,

The good news keeps coming in. I just received an email from the author of the Sopcast client software which contained an updated version of the Linux binary that **includes support for H264 channels**. I will release this as part of SopCast Player just as soon as I can test it out a bit. If you can't wait to get your hands on it I have attached a copy of the client software. Just make sure that you have a symlink in your /usr/bin directory named sp-sc that points to the actual location of this file.

Cheers,
Jason

Whoa!  Your attached binary is v3.2.6 which isn't even released on the sopcast website yet.  Is this a beta?  I'm surprised to see a Linux version supporting H.264, tell your sopcast buddies thanks!

---

### Post by flyguy97 on 2009-11-13
> **mocha said:**
> Whoa!  Your attached binary is v3.2.6 which isn't even released on the sopcast website yet.  Is this a beta?  I'm surprised to see a Linux version supporting H.264, tell your sopcast buddies thanks!

I will definitely pass on your appreciation to the folks at sopcast. To answer your question, no, the attached binary is not a beta. It was finalized 3 days ago and just hasn't been released to the general public yet. Glad to hear your happy with SopCast Player. I think it is a great platform, I just wish it was open source.

Cheers,
Jason

---

### Post by mocha on 2009-11-13
> **flyguy97 said:**
> I will definitely pass on your appreciation to the folks at sopcast. To answer your question, no, the attached binary is not a beta. It was finalized 3 days ago and just hasn't been released to the general public yet. Glad to hear your happy with SopCast Player. I think it is a great platform, I just wish it was open source.

Cheers,
Jason


There's going to be a lot of happy folks at myp2p!

---

### Post by flyguy97 on 2009-11-13
All,

I am very pleased to announce that my PPA now automates the complete process of installing SopCast Player. This is now the preferred method of installation as updating both the client software and SopCast Player itself will be managed completely transparent to the end-user. I suggest all current users un-install both SopCast Player and sp-auth then re-install through the PPA to make sure you are up-to-date (preferences and bookmarks will be unaffected). Installing the PPA is simple, instructions can be found at [https://launchpad.net/~jason-scheunemann/+archive/ppa]("https://launchpad.net/~jason-scheunemann/+archive/ppa"). Once the PPA installed perform the following:

```

$ sudo apt-get update
$ sudo apt-get install sopcast-player
```

You should now have a fully working version of SopCast Player installed. I'm sure some may wonder why this hasn't been done before. The reason is I didn't realize binaries from closed-source projects could be redistributed as part of open-source projects on Launchpad. A nicely detailed explanation of the policy can be found at [https://answers.launchpad.net/launchpad/+question/52348]("https://answers.launchpad.net/launchpad/+question/52348"). It is great to see Ubuntu isn't limiting the use of great applications based solely on its license.

I plan on updating the player in the coming weeks to include features such as greater bookmark management, opening Sop links directly from Firefox (the most requested feature), and fixing the issues revolving around user preferences being lost. These upgrades will remain transparent to you from now on as long as you regularly update your computer. If you want to just update SopCast Player the command to do that is as follows:

```

$ sudo apt-get update
$ sudo apt-get install sopcast-player
```

I'm sure most of you will enjoy the changes as it will free you from looking for updated package versions. However, if you would like to manually update your computer I will try to keep the [Google Code webpage]("http://code.google.com/p/sopcast-player") as up-to-date as possible.

Cheers,
Jason

---

### Post by realzippy on 2009-11-14
Jason-Thanks again.
Now it works even on Karmic 64bit perfectly!!

---

### Post by juliansuddaby on 2009-11-14
Perfect, works great!

---

### Post by flyguy97 on 2009-11-14
All,

I am very happy to hear people are having better success installing SopCast Player. If anyone has any problems at all please let me know and I will help them get everything figured out. If you are having issues, chances are someone else is as well.

Also, I want to give the users a voice in what they want to see next in SopCast Player. Everything is on the table: bug fixes, enhancements, a complete overhaul, whatever you want, it is up to you, the user. Please just leave a message of what you would like to see improved and at the end of next weekend I will have a pretty good idea of what the most important priorities for SopCast player will be. I will use this to create a road map for a 1.0 release of SopCast Player that I will be sure to share with everyone. I believe this program has become successful only through collaboration, from users and translators to people who have volunteered their time and skills. I truly appreciate everyone's efforts and I want to continue this approach to make this the best product it can be.

Cheers,
Jason

---

### Post by flyguy97 on 2009-11-14
All,

I am pleased to announce that I have added support for Hardy in my PPA. I ask that someone verify everything is working correctly.

Cheers,
Jason

---

### Post by flyguy97 on 2009-11-15
All,

Sorry but I made a mistake in the packaging of sp-auth that resulted in the client software never exiting which resulted in continued bandwidth usage until the computer was restarted. The issue has been fixed and verified in Hardy and Karmic (99% sure it will work on all, but if anyone has problems let me know). Make sure to do a:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

The former command will guarantee you fetch the newest file list from my ppa and the latter will actually perform the upgrade. Sorry for the inconvenience and thank you for your continued support.

Cheers,
Jason

---

### Post by flyguy97 on 2009-11-15
> **flyguy97 said:**
> All,

I am pleased to announce that I have added support for Hardy in my PPA. I ask that someone verify everything is working correctly.

Cheers,
Jason

All,

I can verify that Hardy is now 100% supported. As part of the support the local version of VLC must be upgraded. This will require no action as an updated version of VLC for Hardy is also included in my PPA (version 0.9.9a). If you want your VLC to remain stock I regret to say you will be unable to use SopCast Player.

Cheers,
Jason

P.S. The VLC package is courtesy of Christoph Korn, packages were directly copied from his PPA to my own.

---

### Post by mocha on 2009-11-16
Feature requests:

-  Ability to record channels from guide AND any external sop links pasted in by the user.

-  Ability to schedule the recording start/stop times.

Thanks.

---

### Post by flyguy97 on 2009-11-18
> **mocha said:**
> Feature requests:

-  Ability to record channels from guide AND any external sop links pasted in by the user.

-  Ability to schedule the recording start/stop times.

Thanks.

It looks like this might be the number one request. It is close between this and firefox integration.

Cheers,
Jason

---

### Post by Canto39 on 2009-11-18
The Key ID doesnt work for me, what is it?

---

### Post by flyguy97 on 2009-11-19
> **Canto39 said:**
> The Key ID doesnt work for me, what is it?

If your asking about the pgp key for my PPA do the following:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
```

Thank you for pointing this out, I will add these instructions to my Google Code How-to page.

Cheers,
Jason

---

### Post by shajip88 on 2009-11-21
dude u rock. i was about to install windows because of this sopcast  prob but u made me to remain with ubunutu. thanks a lot

---

### Post by flyguy97 on 2009-11-21
> **shajip88 said:**
> dude u rock. i was about to install windows because of this sopcast  prob but u made me to remain with ubunutu. thanks a lot

That is one of the best compliments I have received from this program. I'm glad you'll remain with us. Happy sopcasting!

Cheers,
Jason

---

### Post by gwilkins82 on 2009-11-21
Jason,

I seem to have the some what common problem of the connecting/retrying channel loop for all channels..even the one you listed a while back in the thread for generally always working.  Pretty sure one in particular I am trying is up and running.  Any ideas?  Also, is there a new default for the channel guide?

Thanks a lot!

on a side note, what would i need to do to get vlc to serve as the player?  seems to be what people do based on this thread.

---

### Post by chaopoch on 2009-11-22
I install sopcast-player by adding the PPA to the sources.list, but it is always connecting/retrying, and no channel is available to watch.

BTW, I notice that the /usr/share/sp-auth is blank, if this directory is useless, why is it packed in the package?

---

### Post by chaopoch on 2009-11-22
As you can see in the screenshots, I can watch HuNan TV in gsopcast, but can not in sopcast-player.

[ATTACH]137259[/ATTACH]
[ATTACH]137260[/ATTACH]

---

### Post by flyguy97 on 2009-11-23
> **chaopoch said:**
> I install sopcast-player by adding the PPA to the sources.list, but it is always connecting/retrying, and no channel is available to watch.

BTW, I notice that the /usr/share/sp-auth is blank, if this directory is useless, why is it packed in the package?

I know I need to clean up the sp-auth package a bit, sorry for the slop.

Cheers,
Jason

---

### Post by flyguy97 on 2009-11-23
> **chaopoch said:**
> As you can see in the screenshots, I can watch HuNan TV in gsopcast, but can not in sopcast-player.

[ATTACH]137259[/ATTACH]
[ATTACH]137260[/ATTACH]

I can't explain why it is not working for you. I tried Hunan TV and everything loaded very quickly. Are you able to reach other channels?

Cheers,
Jason

---

### Post by TheFlamingBush on 2009-11-23
Top work Jason....awesome mate!!!!

just a quick question though jason, when opening direct links from firefox, how do i get firefox to recognize the (sop) protocol?

---

### Post by flyguy97 on 2009-11-23
> **TheFlamingBush said:**
> Top work Jason....awesome mate!!!!

just a quick question though jason, when opening direct links from firefox, how do i get firefox to recognize the (sop) protocol?

For an overview of how to do this manually go to the bottom of [http://code.google.com/p/sopcast-player/wiki/Installation]("http://code.google.com/p/sopcast-player/wiki/Installation"). The good news on this is over the weekend I found out how to do this automatically during installation, I just have to re-package and put a new release. I hope to get an update out soon. Thank you for using SopCast Player.

Cheers,
Jason

---

### Post by flyguy97 on 2009-11-23
All,

SopCast Player 0.3.3 has been released. Changes are as follows:

- Usability enhancement patch by Benjamin Klüglein
- Sop links automatically handled by browsers

Cheers,
Jason

---

### Post by chaopoch on 2009-11-23
> **flyguy97 said:**
> I can't explain why it is not working for you. I tried Hunan TV and everything loaded very quickly. Are you able to reach other channels?

Cheers,
Jason

That is really weird, I completely remove the sopcast-player and all the dependencies, then install the new version 0.3.3, but the problem persists, no channel is available, it is always connecting and retrying, what happens?

PS: gsopcast still works normally.

---

### Post by flyguy97 on 2009-11-24
> **chaopoch said:**
> That is really weird, I completely remove the sopcast-player and all the dependencies, then install the new version 0.3.3, but the problem persists, no channel is available, it is always connecting and retrying, what happens?

PS: gsopcast still works normally.

Try opening sopcast-player from the command line and then open a channel. If there are errors they should show up here.

---

### Post by chaopoch on 2009-11-24
> **flyguy97 said:**
> Try opening sopcast-player from the command line and then open a channel. If there are errors they should show up here.

Here is the screenshot for your reference.

[ATTACH]137413[/ATTACH]

---

### Post by chaopoch on 2009-11-24
Here is the screenshot of opening gsopcast from the command line.

[ATTACH]137415[/ATTACH]

---

### Post by flyguy97 on 2009-11-24
> **chaopoch said:**
> Here is the screenshot for your reference.

[ATTACH]137413[/ATTACH]

Are you able to watch any channels?

---

### Post by chaopoch on 2009-11-24
> **flyguy97 said:**
> Are you able to watch any channels?

No, I can not watch any channel with Sopcast Player.

---

### Post by elmariachi on 2009-11-25
I'm on Karmic 64 and I have the same outcome as "chaopoch", I did the following steps:
```

sudo apt-get remove sopcast-player
sudo apt-get remove sp-auth
```Installed the PPA and then:
```

sudo apt-get update
sudo apt-get install sopcast-player
```Still didn't work ("Connecting, Retrying"), so I tried to upgrade:

```
sudo apt-get update
sudo apt-get upgrade
```Still doesn't work ("Connecting, Retrying").

Let me know if you need any more information. And thanks for your work!

Mike

---

### Post by codenamenikky on 2009-11-26
I just wanted to say thank you and its a gr8 job

---

### Post by flyguy97 on 2009-11-26
> **elmariachi said:**
> I'm on Karmic 64 and I have the same outcome as "chaopoch", I did the following steps:
```

sudo apt-get remove sopcast-player
sudo apt-get remove sp-auth
```Installed the PPA and then:
```

sudo apt-get update
sudo apt-get install sopcast-player
```Still didn't work ("Connecting, Retrying"), so I tried to upgrade:

```
sudo apt-get update
sudo apt-get upgrade
```Still doesn't work ("Connecting, Retrying").

Let me know if you need any more information. And thanks for your work!

Mike

This is for both you and chaopoch. Please try the following command to remove sp-auth and sopcast-player:

```

$ sudo aptitude purge sopcast-player
$ sudo aptitude purge sp-auth
$ sudo aptitude clean
```

I'm thinking it may be related to previous versions of sp-auth and sopcast-player. The purge completely removes the package and related files from your system (its a bit more thorough than just a standard remove command). The clean command removes all cached packages retrieved from your package manager (old packages you already have installed).

After you do that perform the following:
```
$ sudo apt-get install sopcast-player
```

This will ensure you get a fresh copy of the packages. Let me know how it goes.

Cheers,
Jason

---

### Post by chaopoch on 2009-11-26
> **flyguy97 said:**
> This is for both you and chaopoch. Please try the following command to remove sp-auth and sopcast-player:

```

$ sudo aptitude purge sopcast-player
$ sudo aptitude purge sp-auth
$ sudo aptitude clean
```

I'm thinking it may be related to previous versions of sp-auth and sopcast-player. The purge completely removes the package and related files from your system (its a bit more thorough than just a standard remove command). The clean command removes all cached packages retrieved from your package manager (old packages you already have installed).

After you do that perform the following:
```
$ sudo apt-get install sopcast-player
```

This will ensure you get a fresh copy of the packages. Let me know how it goes.

Cheers,
Jason


Nothing changes, the problem persists.

---

### Post by flyguy97 on 2009-11-26
> **chaopoch said:**
> Nothing changes, the problem persists.

From the command line type:
```
$ sp-sc sop://211.152.36.38:3912/6022 8901 8902 > test.txt
```

Let it run for a while (about two minutes) and then do a ctrl+c in the terminal to stop the program. Attach the resulting text file (test.txt).

I have to be honest I have no idea of what is going on. I also run Karmic 64 and haven't experienced any issues. Don't worry though, we'll get it figured out.

Cheers,
Jason

---

### Post by chaopoch on 2009-11-26
> **flyguy97 said:**
> from the command line type:
```
$ sp-sc sop://211.152.36.38:3912/6022 8901 8902 > test.txt
```

let it run for a while (about two minutes) and then do a ctrl+c in the terminal to stop the program. Attach the resulting text file (test.txt).

I have to be honest i have no idea of what is going on. I also run karmic 64 and haven't experienced any issues. Don't worry though, we'll get it figured out.

Cheers,
jason

[attach]137713[/attach]

---

### Post by flyguy97 on 2009-11-26
> **Canto39 said:**
> The Key ID doesnt work for me, what is it? 

That is HunanTV, now try:
```
$ sp-sc sop://211.152.36.38:3912/6022 8901 8902 > test.txt
```

And post your results.

Cheers,
Jason

---

### Post by flyguy97 on 2009-11-26
Disregard previous. Go to edit -> preferences -> Channel Guide and change the Channel Guide URL to [http://channel.sopcast.com/gchlxml](http://channel.sopcast.com/gchlxml), refresh and then try some of the channels.

Cheers,
Jason

---

### Post by HuaiDan on 2009-11-27
Works great, but would it be possible to post a comprehensive guide?

---

### Post by flyguy97 on 2009-11-28
> **HuaiDan said:**
> Works great, but would it be possible to post a comprehensive guide?

What kind of information would you be looking for in the guide?

---

### Post by flyguy97 on 2009-11-28
> **chaopoch said:**
> [attach]137713[/attach]

Now in SopCast Player select File -> Open and type in the same sop address as you used on the command line (sop://211.152.36.38:3912/6022). Let me know if it works for you.

Cheers,
Jason

---

### Post by Yunus Emre on 2009-11-28
Here is the good news: I've started Turkish translation. :)

---

### Post by flyguy97 on 2009-11-28
> **Yunus Emre said:**
> Here is the good news: I've started Turkish translation. :)

Excellent, I will release a new version whenever you are completed.

Cheers,
Jason

---

### Post by chaopoch on 2009-11-28
> **flyguy97 said:**
> Now in SopCast Player select File -> Open and type in the same sop address as you used on the command line (sop://211.152.36.38:3912/6022). Let me know if it works for you.

Cheers,
Jason

Yes, it works by typing the address in File -> Open, but it still does not work while opening it in the channel guide, why?

[ATTACH]137848[/ATTACH]

---

### Post by flyguy97 on 2009-11-28
> **chaopoch said:**
> Yes, it works by typing the address in File -> Open, but it still does not work while opening it in the channel guide, why?

[ATTACH]137848[/ATTACH]

To answer that I need to know a couple of things. What country do you live in and what localization are you using for your user profile?

---

### Post by chaopoch on 2009-11-28
> **flyguy97 said:**
> To answer that I need to know a couple of things. What country do you live in and what localization are you using for your user profile?

1. I live in Taiwan

2. localization? are you talking about "locale'? if you are, the Locale is "zh_TW.UTF-8".

3. Sopcast Player worked perfectly in Ubuntu 9.04 (VLC 1.0.1), I upgraded the whole system to 9.10 (VLC 1.0.2), and then Sopcast player never works normally, first problem was dual windows, but I can opened all the channels, now the dual windows problem is fixed, but no channel is available to watch.

4. Why don't use MPlayer as the default player? and why can not MPlayer integrate into the Sopcast Player interface?

---

### Post by flyguy97 on 2009-11-28
> **chaopoch said:**
> 1. I live in Taiwan

2. localization? are you talking about "locale'? if you are, the Locale is "zh_TW.UTF-8".

3. Sopcast Player worked perfectly in Ubuntu 9.04 (VLC 1.0.1), I upgraded the whole system to 9.10 (VLC 1.0.2), and then Sopcast player never works normally, first problem was dual windows, but I can opened all the channels, now the dual windows problem is fixed, but no channel is available to watch.

4. Why don't use MPlayer as the default player? and why can not MPlayer integrate into the Sopcast Player interface?

I tried to use MPlayer but there were serious issues with the sound and video becoming out of sync. VLC is able to remain in sync for a majority of the time and even when it does occasionally experience an out of sync condition it will self-correct.

The issue with the channel guide is that since you are using the zh_TW locale SopCast Player defaults to using [http://channel.sopcast.com/gchlxml](http://channel.sopcast.com/gchlxml) as the channel guide instead of [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml). Please change the channel guide url in Edit -> Preferences, refresh the channel guide, and let me know if that fixes your issues.

Cheers,
Jason

---

### Post by chaopoch on 2009-11-28
> **flyguy97 said:**
> I tried to use MPlayer but there were serious issues with the sound and video becoming out of sync. VLC is able to remain in sync for a majority of the time and even when it does occasionally experience an out of sync condition it will self-correct.

The issue with the channel guide is that since you are using the zh_TW locale SopCast Player defaults to using [http://channel.sopcast.com/gchlxml](http://channel.sopcast.com/gchlxml) as the channel guide instead of [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml). Please change the channel guide url in Edit -> Preferences, refresh the channel guide, and let me know if that fixes your issues.

Cheers,
Jason

I test some channels, but only HuNan TV (sop://211.152.36.38:3912/6022) can be watched, the rest are always "connecting".

[ATTACH]137874[/ATTACH]

---

### Post by flyguy97 on 2009-11-28
> **chaopoch said:**
> I test some channels, but only HuNan TV (sop://211.152.36.38:3912/6022) can be watched, the rest are always "connecting".

[ATTACH]137874[/ATTACH]

What is the current URL for your channel guide?

---

### Post by JacobK on 2009-11-28
When I try to install the .deb for sp-auth 3.0.1 on ubuntu 9.10 it says: "Error: Dependency is not satisfiable: ia32-libs|lib32stdc++5". Can someone explain what the problem is?

---

### Post by flyguy97 on 2009-11-28
> **JacobK said:**
> When I try to install the .deb for sp-auth 3.0.1 on ubuntu 9.10 it says: "Error: Dependency is not satisfiable: ia32-libs|lib32stdc++5". Can someone explain what the problem is?

It is best to install my ppa to handle depenecies automatically. See the instructions at [http://code.google.com/p/sopcast-player/wiki/Installation](http://code.google.com/p/sopcast-player/wiki/Installation). Let me know if you have any troubles.

Cheers,
Jason

---

### Post by JacobK on 2009-11-28
I'm not a hardcore ubuntu-user, can you give a step-by-step explanation what I should with the commands? thanks for the help!

---

### Post by flyguy97 on 2009-11-28
> **JacobK said:**
> I'm not a hardcore ubuntu-user, can you give a step-by-step explanation what I should with the commands? thanks for the help!

I would be happy to help. The first thing you need to know is that anytime you see the dollar sign ($) at the beginning of a line this usually means that whatever follows should be executed with a terminal window. To get to a terminal go to Applications -> Accessories -> Terminal. You may at times see the pound symbol (#) this indicates the following commands should also be executed at the terminal but as the root user. There is a command that will make you the root user just for one command and that is sudo. Whatever command following the pound can also be executed by using sudo. For example

```
# lspci
```

and

```
$ sudo lspci
```

are equivalent commands

With that said, any command performed as the root user should be carefully scrutinized prior to execution.

The two commands to execute to add my ppa are:

```
$ echo "deb http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu `lsb_release -cs` main" | sudo tee -a /etc/apt/sources.list
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
``` 

The first line adds my ppa to your software sources file and the second command adds my ppa key to your software sources keyring.

The only thing left to do now is install my software, this can be done by executing the following command:

```
$ sudo apt-get install sopcast-player
```

Note: When typing commands into the terminal be sure not to include the opening # or $ as these are just indicators of account access to be used during execution.

Good luck and please let me know if you need any additional assistance.

Cheers,
Jason

---

### Post by JacobK on 2009-11-28
Awesome! It works! You give more than enough information actually, I knew all the stuff about terminal and sudo already, but for some reason the installation didn't work before.

Thanks for the help!

---

### Post by flyguy97 on 2009-11-28
> **JacobK said:**
> Awesome! It works! You give more than enough information actually, I knew all the stuff about terminal and sudo already, but for some reason the installation didn't work before.

Thanks for the help!

No problem, glad to help. Thank you for your interest in SopCast Player.

Cheers,
Jason

---

### Post by chaopoch on 2009-11-28
> **flyguy97 said:**
> What is the current URL for your channel guide?


As you mentioned,

[http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)

---

### Post by c-m on 2009-11-29
I added your ppa and i'm getting the following error:

W: Failed to fetch [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/helena/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/helena/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by flyguy97 on 2009-11-29
> **c-m said:**
> I added your ppa and i'm getting the following error:

W: Failed to fetch [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/helena/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/helena/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

c-m,

Nice to see a fellow Norfolker in here. What distribution are you using?

---

### Post by c-m on 2009-11-29
I used to use 9.04 but and had this all working perfectly.

I recently moved to fresh install of Linux Mint 9.10

---

### Post by flyguy97 on 2009-11-29
> **c-m said:**
> I used to use 9.04 but and had this all working perfectly.

I recently moved to fresh install of Linux Mint 9.10

The command you ran is for Ubuntu only, remove the line you added in /etc/apt/sources.list and run the following from a command line:

```
echo "deb http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu jaunty main" | sudo tee -a /etc/apt/sources.list
```

This is assuming you are using the latest version of mint.

Be sure to do a sudo apt-get update then sudo apt-get install sopcast-player.

Cheers,
Jason

---

### Post by c-m on 2009-11-29
The latest version of mint (mint 8) is based on Karmic not Jaunty.

I followed your command but it complains that ap-auth is missing. 


```

carl@desktop ~ $ sudo apt-get install sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  sopcast-player: Depends: sp-auth (>= 3.0.1) but it is not going to be installed
E: Broken packages
carl@desktop ~ $ 

``` 

I have manually downloaded sp-auth but that can't install as it complains i don't have  ia32-libs|lib32stdc++5

---

### Post by flyguy97 on 2009-11-29
> **c-m said:**
> The latest version of mint (mint 8) is based on Karmic not Jaunty.

I followed your command but it complains that ap-auth is missing. 


```

carl@desktop ~ $ sudo apt-get install sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  sopcast-player: Depends: sp-auth (>= 3.0.1) but it is not going to be installed
E: Broken packages
carl@desktop ~ $ 

``` 

I have manually downloaded sp-auth but that can't install as it complains i don't have  ia32-libs|lib32stdc++5


Try to do a apt-get remove --purge sp-auth then retry apt-get install sopcast-player.

---

### Post by c-m on 2009-11-29
Same result unfortunately.

I tried to find ia32-libs|lib32stdc++5 in synaptic but they aren't there.

My apt list is as follows:

```


deb http://packages.linuxmint.com/ helena main upstream import
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ karmic partner
deb http://packages.medibuntu.org/ karmic free non-free


deb http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu jaunty main

```

---

### Post by flyguy97 on 2009-11-29
> **c-m said:**
> Same result unfortunately.

I tried to find ia32-libs|lib32stdc++5 in synaptic but they aren't there.

My apt list is as follows:

```


deb http://packages.linuxmint.com/ helena main upstream import
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ karmic partner
deb http://packages.medibuntu.org/ karmic free non-free


deb http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu jaunty main

```

If your mint distribution is based on Karmic then replace the part of my ppa line that reads jaunty with karmic. ia-libs32 no longer includes lib32stdc++5 in Karmic, my ppa provides this package. Let me know how it works for you.

Cheers,
Jason

---

### Post by c-m on 2009-11-29
Works perfectly. Thanks.

---

### Post by flyguy97 on 2009-11-29
> **c-m said:**
> Works perfectly. Thanks.

No problem. Happy sopcsating!!

Cheers,
Jason

---

### Post by mantorpcity on 2009-12-02
Thanks for this app, got it working just in time to see my Spurs lose to Man U. Anyone know a command to get it to use vlc as the external player?

---

### Post by flyguy97 on 2009-12-02
> **mantorpcity said:**
> Thanks for this app, got it working just in time to see my Spurs lose to Man U. Anyone know a command to get it to use vlc as the external player?

I didn't write in anything special to handle an external player from the command line. However, if you launch it from the command line it should retain its previous configuration. In other words, configure for external player before trying to use from command line.

Cheers,
Jason

---

### Post by rattatti on 2009-12-06
I had been using this great app for some time without any problems, but recently I have been having some problems. The thing is when I start a channel it does not seem to buffer enough to be watchable and I get these errors.
```

swScaler: Palette is not supported as output pixel format
[0xb5a009e0] swscale scale error: could not init SwScaler and/or allocate memory
[0x8e89ea8] pulse audio output: No. of Audio Channels: 2
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/VLCWidget.py", line 33, in handle_embed
    self.player.set_xwindow(self.window.xid)
AttributeError: 'MediaControl' object has no attribute 'set_xwindow'
[0x8d5a5b0] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 1200 ms
[0x8d5a5b0] main input error: ES_OUT_RESET_PCR called
[0x8d5a5b0] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 1802 ms
[0x8d5a5b0] main input error: ES_OUT_RESET_PCR called

```I am running Ubuntu 9.10 Karmic Koala, but I have another machine with 9.04 that runs sopcast-player without any problems.

Any ideas what I can do to get rid of the errors?

Thanks

---

### Post by flyguy97 on 2009-12-06
> **mantorpcity said:**
> Thanks for this app, got it working just in time to see my Spurs lose to Man U. Anyone know a command to get it to use vlc as the external player?

mantorpcity,

I apologize, it looks like I may have misread your post. The command to get vlc working is just vlc. You don't have to worry about adding the stream location, that is taken care of for you. If you want other options you can just add them in as command line switches. The following are some examples:

VLC with no switches
```
vlc
```

VLC always on top of other windows
```
vlc --video-on-top
```

VLC starting in fullscreen
```
vlc --fulscreen
```

With enough experimenting you should be able to get VLC to behave the way you would like, I'm pretty sure it is even possible to setup recording through the command-line switches. If you come up with some interesting uses please post. Thank you and happy sopcasting.

Cheers,
Jason

---

### Post by elmariachi on 2009-12-13
Hi Jason,

Thanks for your work on this - it seems to be working after doing all the purging and one extra step: clicking the Channel Refresh arrow next to the Sopcast Player Channel Guide.

For your information, like Chaopoch, I'm also in Taiwan.

Mike

---

### Post by flyguy97 on 2009-12-13
> **elmariachi said:**
> Hi Jason,

Thanks for your work on this - it seems to be working after doing all the purging and one extra step: clicking the Channel Refresh arrow next to the Sopcast Player Channel Guide.

For your information, like Chaopoch, I'm also in Taiwan.

Mike

Glad to hear you got this working. Through some of these issues I was able to find a better understanding of Taiwan's political standing with China, very interesting! An unanticipated but welcome result of the open source community!

Cheers,
Jason

---

### Post by misGnomer on 2009-12-22
I had a working configuration of Sopcast and VLC ( 0.9.8 ) on Hardy 8.04 LTS, but seeing that you had put updated versions of both on your PPA I thought I'd give it a go.

Unfortunately the Hardy package of VLC 0.9.9 (which is borrowed from Christoph Korn's PPA) seems to have a quarrel with itself, ending up with broken packages.


Short version:

```
E: /var/cache/apt/archives/libvlccore0_0.9.9a-1~ppa1~hardy5_i386.deb: trying to overwrite `/usr/lib/libvlccore.so.0', which is also in package libvlc0
E: /var/cache/apt/archives/libvlc2_0.9.9a-1~ppa1~hardy5_i386.deb: trying to overwrite `/usr/lib/libvlc.so.2', which is also in package libvlc0
```


Long version:

```
Unpacking libvlccore0 (from .../libvlccore0_0.9.9a-1~ppa1~hardy5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libvlccore0_0.9.9a-1~ppa1~hardy5_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libvlccore.so.0', which is also in package libvlc0
Unpacking libvlc2 (from .../libvlc2_0.9.9a-1~ppa1~hardy5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libvlc2_0.9.9a-1~ppa1~hardy5_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libvlc.so.2', which is also in package libvlc0
Selecting previously deselected package libvlccore-dev.
Unpacking libvlccore-dev (from .../libvlccore-dev_0.9.9a-1~ppa1~hardy5_i386.deb) ...
Selecting previously deselected package libvlc-dev.
Unpacking libvlc-dev (from .../libvlc-dev_0.9.9a-1~ppa1~hardy5_i386.deb) ...
Selecting previously deselected package sp-auth.
Unpacking sp-auth (from .../sp-auth_3.2.6~ppa1~hardy8_i386.deb) ...
Selecting previously deselected package sopcast-player.
Unpacking sopcast-player (from .../sopcast-player_0.3.3~ppa1~hardy3_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libvlccore0_0.9.9a-1~ppa1~hardy5_i386.deb
 /var/cache/apt/archives/libvlc2_0.9.9a-1~ppa1~hardy5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libvlccore-dev:
 libvlccore-dev depends on libvlccore0 (= 0.9.9a-1~ppa1~hardy5); however:
  Package libvlccore0 is not installed.
dpkg: error processing libvlccore-dev (--configure):
 dependency problems - leaving unconfigured
Setting up sp-auth (3.2.6~ppa1~hardy8) ...
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libvlc2 (>= 0.9.1); however:
  Package libvlc2 is not installed.
 vlc-nox depends on libvlccore0 (>= 0.9.1); however:
  Package libvlccore0 is not installed.
dpkg: error processing vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libvlc-dev:
 libvlc-dev depends on libvlc2 (= 0.9.9a-1~ppa1~hardy5); however:
  Package libvlc2 is not installed.
 libvlc-dev depends on libvlccore-dev; however:
  Package libvlccore-dev is not configured yet.
dpkg: error processing libvlc-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on libvlccore0 (>= 0.9.1); however:
  Package libvlccore0 is not installed.
 vlc depends on vlc-nox (= 0.9.9a-1~ppa1~hardy5); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sopcast-player:
 sopcast-player depends on libvlc-dev; however:
  Package libvlc-dev is not configured yet.
 sopcast-player depends on vlc (>= 0.9.4); however:
  Package vlc is not configured yet.
dpkg: error processing sopcast-player (--configure):
 dependency problems - leaving unconfigured
```


In fact despite broken packages I could still run VLC 0.9.9 (as a temporary test), but sopcast-player failed to start altogether.

```
$ sopcast-player 
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 38, in <module>
    import vlc
  File "/usr/share/sopcast-player/lib/vlc.py", line 46, in <module>
    dll=ctypes.CDLL('libvlc.so')
  File "/usr/lib/python2.5/ctypes/__init__.py", line 348, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: libvlc.so: cannot open shared object file: No such file or directory
$ 

```

Apparently I've been naughty so no Sopcast for me over the holidays.  :-\"

---

### Post by hullpaul on 2010-01-08
thank you, thank you thank you, couldnt get it to work no matter what i tried (tho i only switched to linux a week ago) but this loaded straight away and just in time for this weekends football, which has just been cancelled ffs!

---

### Post by flyguy97 on 2010-01-09
> **hullpaul said:**
> thank you, thank you thank you, couldnt get it to work no matter what i tried (tho i only switched to linux a week ago) but this loaded straight away and just in time for this weekends football, which has just been cancelled ffs!

hullpaul,

Glad to hear it worked out for your and welcome to the Linux community.

Warm Regards,
Jason

---

### Post by psablo on 2010-01-11
Great App!
I was skeptical at first due to the third party repository but, what the heck I'll trust you.

---

### Post by flyguy97 on 2010-01-12
> **psablo said:**
> Great App!
I was skeptical at first due to the third party repository but, what the heck I'll trust you.

psablo,

Glad to have you on board, I hope you like the app. Let me know if you have any troubles or any suggestions on how to improve SopCast Player.

Cheers,
Jason

---

### Post by nicknefarious on 2010-01-24
> **flyguy97 said:**
> I tried to use MPlayer but there were serious issues with the sound and video becoming out of sync. VLC is able to remain in sync for a majority of the time and even when it does occasionally experience an out of sync condition it will self-correct.

The issue with the channel guide is that since you are using the zh_TW locale SopCast Player defaults to using [http://channel.sopcast.com/gchlxml](http://channel.sopcast.com/gchlxml) as the channel guide instead of [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml). Please change the channel guide url in Edit -> Preferences, refresh the channel guide, and let me know if that fixes your issues.

Cheers,
Jason

I too am in China... (Taiwan is or isnt' a part of China - not my argument).

I installed Sopcast and had the problem that said the Channel server was down and changed from the [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml) to the [http://channel.sopcast.com/gchlxml](http://channel.sopcast.com/gchlxml) and channels seem to be working. I did have a problem when I tried to change to another channel the python package started eating up 100% of one of my processors I had to force quit it. Also I have two screens opening with the feed presented on both of them. How do I fix this? Or do I just need to read further?

Cheers,

Nick

---

### Post by flyguy97 on 2010-01-24
Nick,

Did you install from my PPA. It sounds like your running an older version of SopCast Player. See the instructions at [[http://code.google.com/p/sopcast-player/wiki/Installation]](http://code.google.com/p/sopcast-player/wiki/Installation]) for detailed instructions on how to ensure your running the latest version of SopCast Player. Please let me know if this works for you.

Warm regards,
Jason

> **nicknefarious said:**
> I too am in China... (Taiwan is or isnt' a part of China - not my argument).

I installed Sopcast and had the problem that said the Channel server was down and changed from the [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml) to the [http://channel.sopcast.com/gchlxml](http://channel.sopcast.com/gchlxml) and channels seem to be working. I did have a problem when I tried to change to another channel the python package started eating up 100% of one of my processors I had to force quit it. Also I have two screens opening with the feed presented on both of them. How do I fix this? Or do I just need to read further?

Cheers,

Nick

---

### Post by nicknefarious on 2010-01-24
> **flyguy97 said:**
> Nick,

Did you install from my PPA. It sounds like your running an older version of SopCast Player. See the instructions at [[http://code.google.com/p/sopcast-player/wiki/Installation]](http://code.google.com/p/sopcast-player/wiki/Installation]) for detailed instructions on how to ensure your running the latest version of SopCast Player. Please let me know if this works for you.

Warm regards,
Jason
Hi Jason,

You were right. When I ran the update this morning your PPA kicked in and wanted to download and install your newer packages and this caused a conflict with the existing packages. I uninstalled and removed all. Reloaded and then reinstalled sopcast-player and sp-auth all from your PPA. Now the channel guide appears, it is able to update the channel database but most of the channels do not load. They are forever connecting. 

I was able to open this - [http://channel.sopcast.com/gchlxml]("http://channel.sopcast.com/gchlxml") in my browser (unable to surf to the default channel server) and retrieve a channel from it and use cut and paste it in the 'open' function of sopcast's menu and it worked - but I fear the same as chaopoch. I am unable to open them through the channel guide. One of the Chinese channels opened through the guide initially - but it took a LONG time - maybe 5 minutes and I think (sorry I am not sure) it was while I still had the default channel server url in.

Update: Just got National Geographic Page to load by finding the url in the browser page (as above) and cutting and pasting across. It still took 2 or 3 minutes though. It seems I cannot reconnect (added note - connected after 8 minutes) to this channel by clicking on the channel in the channel guide. So two questions... What is the problem with the channel guide? Is it normal for channels to take that long to connect? I used to use sopcast in XP also here in China and it was quick and quality. How can I fix this? Sorry I know that was three...

Cheers,

Nick

PS - Sorry I should have said that your new packages removed the two screen problem. The only problem I seem to have now is this channel loading time.

---

### Post by flyguy97 on 2010-01-24
Go to Edit -> Preferences -> Channel Guide. Enter the address you stated that is working correctly, [http://channel.sopcast.com/gchlxml]("http://channel.sopcast.com/gchlxml"), into the Channel Guide URL text box. Refresh and please let me know how that works for you.

Warm regards,
Jason

> **nicknefarious said:**
> Hi Jason,

You were right. When I ran the update this morning your PPA kicked in and wanted to download and install your newer packages and this caused a conflict with the existing packages. I uninstalled and removed all. Reloaded and then reinstalled sopcast-player and sp-auth all from your PPA. Now the channel guide appears, it is able to update the channel database but most of the channels do not load. They are forever connecting. 

I was able to open this - [http://channel.sopcast.com/gchlxml]("http://channel.sopcast.com/gchlxml") in my browser (unable to surf to the default channel server) and retrieve a channel from it and use cut and paste it in the 'open' function of sopcast's menu and it worked - but I fear the same as chaopoch. I am unable to open them through the channel guide. One of the Chinese channels opened through the guide initially - but it took a LONG time - maybe 5 minutes and I think (sorry I am not sure) it was while I still had the default channel server url in.

Update: Just got National Geographic Page to load by finding the url in the browser page (as above) and cutting and pasting across. It still took 2 or 3 minutes though. It seems I cannot reconnect (added note - connected after 8 minutes) to this channel by clicking on the channel in the channel guide. So two questions... What is the problem with the channel guide? Is it normal for channels to take that long to connect? I used to use sopcast in XP also here in China and it was quick and quality. How can I fix this? Sorry I know that was three...

Cheers,

Nick

PS - Sorry I should have said that your new packages removed the two screen problem. The only problem I seem to have now is this channel loading time.

---

### Post by nicknefarious on 2010-01-24
> **flyguy97 said:**
> Go to Edit -> Preferences -> Channel Guide. Enter the address you stated that is working correctly, [http://channel.sopcast.com/gchlxml]("http://channel.sopcast.com/gchlxml"), into the Channel Guide URL text box. Refresh and please let me know how that works for you.

Warm regards,
Jason
Again apologies... I should have been more specific. I have already done this as per your previous instructions to Chaopoch and others.

The problem exists still. Even other sop links take forever or don't load at all.

Should I be able to open this in sopcast? - sop://broker1.sopcast.com:3912/77551 - I can't. Most of the others take a LONG time or don't open (most never open - just always connecting then retrying). Either through direct entry of the sop url or through the channel guide.

Cheers for your quick reply help too...

Nick

---

### Post by max69 on 2010-01-25
Works a treat!!! Thanks a lot!!!!

---

### Post by Banhammer on 2010-01-25
Just got this set up and works great. Can't thank you enough for making this happen.

---

### Post by flyguy97 on 2010-01-26
max69, Banhammer,

I am glad you both enjoy the application. Please let me know if you see anything that can be improved.

Warm Regards,
Jason

---

### Post by Taman on 2010-02-06
Hi all. I've the same problem like Chaopoch too. I try every method you suggest but it still connect/retry.

when i try to run sopcast-player in terminal and wait for a long time. I got this message in terminal

---

### Post by Canto39 on 2010-02-07
I couldnt get this to work until I set it to play through VLC and it worked perfectly! Thanks for this.

---

### Post by mercier on 2010-02-07
first of all, thanks jason for your hard work. sopcast on linux was the last thing that kept me from fully switching from windows ;)

i use your app on linuxmint 8, works as a charm. i do have one issue that bugs me - i am unable to change aspect ratio on streams i watch, either through mplayer, or external player - in my case vlc.

can you, or anyone else, help me solve this?

(i went through vlc --help files and terminal commands, but couldn't find a solution)

Thanks in advance

M.

---

### Post by flyguy97 on 2010-02-08
Mercier,

I am glad to hear that you are having a positive experience with Linux, I am very excited that SopCast Player helped influence your decision to switch.

About your question addressing aspect ratio. I never really considered if that is possible. The stream itself is only offered in one format but it is conceivable to use vlc or mplayer to crop the video into an aspect ratio of your choice. I've included a link that details how to change the default fullscreen aspect ratio in vlc. I will also look into adding a setting that will allow the user to choose a standard aspect ratio. No promises on when I will be able to release an update though. Things at work are a bit busy right now.

[http://ubuntuforums.org/showthread.php?t=725160]("http://ubuntuforums.org/showthread.php?t=725160")

Warm Regards,
Jason

> **mercier said:**
> first of all, thanks jason for your hard work. sopcast on linux was the last thing that kept me from fully switching from windows ;)

i use your app on linuxmint 8, works as a charm. i do have one issue that bugs me - i am unable to change aspect ratio on streams i watch, either through mplayer, or external player - in my case vlc.

can you, or anyone else, help me solve this?

(i went through vlc --help files and terminal commands, but couldn't find a solution)

Thanks in advance

M.

---

### Post by flyguy97 on 2010-02-08
All,

I really appreciate all the warm remarks about this program. In my role as the main programmer of SopCast Player I often hear kind words about my efforts which I truly appreciate. However, my contribution to this project is just a small part of the community effort that has driven its development. Currently this program has been translated into 34 languages. People have contributed code, ideas, bug submissions and artwork to make this program what it is today. The success of this project is a direct reflection on the quality of the individuals that I have been blessed to work with. I sincerely thank everyone that has contributed to this project.

Warmest Regards,
Jason

---

### Post by mockingbird on 2010-02-08
I'm having a problem when I use this app, and it seems to happen with certain channels...

When I connect to them I lose my system audio and even restarting alsa doesn't restore the sound -- I have to reboot.

It's probably VLC's fault.  I'm having to use a lenny-backport version because Lenny is horribly outdated.

---

### Post by flyguy97 on 2010-02-08
> **mockingbird said:**
> I'm having a problem when I use this app, and it seems to happen with certain channels...

When I connect to them I lose my system audio and even restarting alsa doesn't restore the sound -- I have to reboot.

It's probably VLC's fault.  I'm having to use a lenny-backport version because Lenny is horribly outdated.

mockingbird,

You are the second user to report this issue. I believe it is a codec issue. It concerns me however that you stated you are loosing you system audio. Please clarify if you are unable to hear audio with SopCast Player or if it bringing down the audio for your whole system. Assuming it is a codec issue it will be a fairly simple fix if you are using the launchpad ppa for SopCast Player. I will just include whatever codec as a prereq for SopCast Player. If you are not using the ppa you will have to check the google code site for updates. I will be sure to keep everyone posted on the status of this bug.

Warm Regards,
Jason

---

### Post by mockingbird on 2010-02-10
Thanks for the response.  I am losing all system audio, as I indicated that I tried to restart ALSA when this happened but to no avail.

I'm pretty sure it's related to the old version ov VLC I am using (0.9.9).  I am stuck with it at the current moment because that's the only thing available from the Lenny backports.

---

### Post by flyguy97 on 2010-02-10
> **mockingbird said:**
> Thanks for the response.  I am losing all system audio, as I indicated that I tried to restart ALSA when this happened but to no avail.

I'm pretty sure it's related to the old version ov VLC I am using (0.9.9).  I am stuck with it at the current moment because that's the only thing available from the Lenny backports.

I will see if it is possible to port over a newer version of vlc. Please give me the weekend.

Cheers,
Jason

---

### Post by hissyfut on 2010-02-13
is something needed here?

$ sopcast-player 
<code>
(sopcast-player.py:): libglade-WARNING **: could not find glade file '/usr/share/sopcast-player/lib/../ui/SopCastClientMissing.glade'
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 1781, in <module>
    pySop.main()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 508, in main
    self.show_missing_sopcast_client_dialog()		
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 527, in show_missing_sopcast_client_dialog
    tree = gtk.glade.XML(gladefile, "sopcast-client-missing-dialog")
RuntimeError: could not create GladeXML object </code>

---

### Post by mockingbird on 2010-02-17
> **flyguy97 said:**
> I will see if it is possible to port over a newer version of vlc. Please give me the weekend.

Cheers,
Jason

Hi Jason,

Did you have any luck with this?

Thanks

---

### Post by thongkh on 2010-02-22
> **flyguy97 said:**
> mockingbird,

You are the second user to report this issue. I believe it is a codec issue. It concerns me however that you stated you are loosing you system audio. Please clarify if you are unable to hear audio with SopCast Player or if it bringing down the audio for your whole system. Assuming it is a codec issue it will be a fairly simple fix if you are using the launchpad ppa for SopCast Player. I will just include whatever codec as a prereq for SopCast Player. If you are not using the ppa you will have to check the google code site for updates. I will be sure to keep everyone posted on the status of this bug.

Warm Regards,
Jason

help, i lost my SopCast player audio, i using SopCast Player 0.3.3 in my Ubuntu 9.10, i have launchpad ppa for SopCast Player, and i just check the update, but i still lost my SopCast Player audio... please help... :(
btw, i only cant hear audio frm SopCast Player, others audio frm others programe works fine.

*** update ***
i just did my update again today, i dont know what did i updated, but my SopCast Player now have audio... everythings works great now!!!... thankz bro ;)

---

### Post by mockingbird on 2010-03-07
> **mockingbird said:**
> Hi Jason,

Did you have any luck with this?

Thanks

Unlikely.  The newer VLCs have dependencies that just won't fly with older versions of Debian.  I will need Squeeze if I want to run anything past the early 1.x versions.

I answered my own question it seems :D

---

### Post by mercier on 2010-03-14
> **flyguy97 said:**
> Mercier,

I am glad to hear that you are having a positive experience with Linux, I am very excited that SopCast Player helped influence your decision to switch.

About your question addressing aspect ratio. I never really considered if that is possible. The stream itself is only offered in one format but it is conceivable to use vlc or mplayer to crop the video into an aspect ratio of your choice. I've included a link that details how to change the default fullscreen aspect ratio in vlc. I will also look into adding a setting that will allow the user to choose a standard aspect ratio. No promises on when I will be able to release an update though. Things at work are a bit busy right now.

[http://ubuntuforums.org/showthread.php?t=725160]("http://ubuntuforums.org/showthread.php?t=725160")

Warm Regards,
Jason

well, never mind. i have vlc in settings as a separate player and it does open as vlc-proper, with all the options, including change of aspect ratio.

good work, jason.

---

### Post by c-m on 2010-03-16
I'm back struggling with this again. Had to reinstall Mint (based and karmic) 

I have added the repository to my sources.list

I ran apt-get update but it returned:

```
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 932062C9CD30EE56
   
```

So I tried installing the key (whatever that is)

```

 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
gpg: requesting key CD30EE56 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


```

---

### Post by clive littlewood on 2010-03-22
Hi

Has anyone managed to get sopcast player installed in Lucid ???

If so how (I just get strings of missing dependences)

Thanks in hope

Clive

PS.  Fantastic player Jason thanks for your efforts.

PS.PS.  Have sorted out by using the Lucid PPA and installing from synaptic.   THANKS

---

### Post by afrodeity on 2010-03-26
This looks like a conflict with the new VLC 1.1

```
sopcast-player
[0x97b73c8] main libvlc error: No modules were found, refusing to start. Check that you properly gave a module path with --plugin-path.
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 1780, in <module>
    pySop = pySopCast()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 368, in __init__
    self.vlc = VLCWidget.VLCWidget(*p)
  File "/usr/share/sopcast-player/lib/VLCWidget.py", line 28, in __init__
    self.player=instance.mediacontrol_new_from_instance()
AttributeError: 'NoneType' object has no attribute 'mediacontrol_new_from_instance'

```

Not sure exactly how to do this:

sopcast-player --plugin-path ~/.local/share/vlc/lua/extensions/
Segmentation fault

sopcast-player --plugin-path
Usage: sopcast-player [SOP_ADDRESS] [IN-BOUND_PORT OUT-BOUND_PORT]

---

### Post by Rabcnesbit on 2010-03-30
Ok, completely new to Linux, and using Ubuntu 9.10. 
  I have downloaded this software - Sopcast player 0.3.3 (complete file name is sopcast-player-0.3.3-1mdv2010.0.i586.rpm) from [http://code.google.com/p/sopcast-player/](http://code.google.com/p/sopcast-player/), so I hope I have downloaded the right one. I followed the installation instructions, first installing the PPA and then the Sopcast player (didn’t install the Medibuntu repositories at this stage), using the command lines as instructed. Managed to figure out that these command lines go in the ‘Terminal’.  Like I stated before, I am completely new to Linux (have been using windows like most), so this is all still Greek to me. Everything seemed to have gone fine in the terminal window, and I subsequently exited/closed the window. Now, I can’t figure out where this ‘installed’ Sopcast player is, or how to launch it? Any advice please.
   
  Many thanks

---

### Post by clive littlewood on 2010-03-30
Hi

If you have added the PPA for your ubuntu version then the sopcast player should appear in synaptic.

Or from terminal sudo apt-get install sopcast-player

This will also install VLC as the built in player.

I would make sure medibuntu repos are added to your sources.

You should not need the rpm file.

Hope this helps

Clive

---

### Post by Rabcnesbit on 2010-03-30
Thanks Clive,

Followed your suggestions (though not really sure what i was doing) but have managed to get it to start. Now let's go try and get some links working. :)

Cheers

---

### Post by clive littlewood on 2010-03-31
Hi

To add a link just click file > open then copy paste the link into the box.

Glad your up and running.

By adding the PPA you will now get any updates automatically through update manager.

Clive

---

### Post by afrodeity on 2010-03-31
man sopcast-player
No manual entry for sopcast-player
See 'man 7 undocumented' for help when manual pages are not available.

---

### Post by afrodeity on 2010-04-04
Tried removing sopcast-player and sp-auth and reinstalling but no luck. Sigh.

---

### Post by afrodeity on 2010-04-04
I've downgraded sopcast because it was working with an earlier version

now I get this error
```

 File "/usr/share/sopcast-player/lib/sopcast-player.py", line 37, in <module>
    import vlc
ImportError: libvlc.so.2: cannot open shared object file: No such file or directory

```

searching for libvlc.so.2 produces nothing.

searching for libvlc, I have libvlc.so.5 in /usr/lib
and libvlc.so.5.0.0 also in /usr/lib

Should I make a symbolic link, and how?
and

---

### Post by philipos on 2010-04-08
hey, following your instructions i got the following;

philipos@philipos:~$ echo "deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) `lsb_release -cs` main" | sudo tee -a /etc/apt/sources.list
deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) karmic main
philipos@philipos:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
gpg: requesting key CD30EE56 from hkp server keyserver.ubuntu.com
gpg: key CD30EE56: public key "Launchpad PPA for flyguy97" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
philipos@philipos:~$ sudo apt-get install sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sopcast-player
philipos@philipos:~$ sudo apt-get install sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sopcast-player

any idea what's gone wrong here?

---

### Post by joanmunoz on 2010-04-08
Hi!

I have the latest version of Sopcast and VLC through the repos ([http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) karmic main), but I can't manage to launch the VLC window as external player. What is it supposed I have to do? I've put 'vlc.desktop' in the external player option of the Preferences menu, but got no results.

Any help?

Thanks!

Joan

Linux joan-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

---

### Post by flyguy97 on 2010-04-10
After adding repositories you must do a:
```
$ sudo apt-get update
```

This will pull all the latest package information from the PPA, until this step is completed apt doesn't know about the packages contained in the ppa.

Cheers,
Jason

> **philipos said:**
> hey, following your instructions i got the following;

philipos@philipos:~$ echo "deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) `lsb_release -cs` main" | sudo tee -a /etc/apt/sources.list
deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) karmic main
philipos@philipos:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
gpg: requesting key CD30EE56 from hkp server keyserver.ubuntu.com
gpg: key CD30EE56: public key "Launchpad PPA for flyguy97" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
philipos@philipos:~$ sudo apt-get install sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sopcast-player
philipos@philipos:~$ sudo apt-get install sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sopcast-player

any idea what's gone wrong here?

---

### Post by flyguy97 on 2010-04-10
What distribution of linux are you running?

> **Rabcnesbit said:**
> Ok, completely new to Linux, and using Ubuntu 9.10. 
  I have downloaded this software - Sopcast player 0.3.3 (complete file name is sopcast-player-0.3.3-1mdv2010.0.i586.rpm) from [http://code.google.com/p/sopcast-player/](http://code.google.com/p/sopcast-player/), so I hope I have downloaded the right one. I followed the installation instructions, first installing the PPA and then the Sopcast player (didn’t install the Medibuntu repositories at this stage), using the command lines as instructed. Managed to figure out that these command lines go in the ‘Terminal’.  Like I stated before, I am completely new to Linux (have been using windows like most), so this is all still Greek to me. Everything seemed to have gone fine in the terminal window, and I subsequently exited/closed the window. Now, I can’t figure out where this ‘installed’ Sopcast player is, or how to launch it? Any advice please.
   
  Many thanks

---

### Post by oobuntoo on 2010-04-10
I'm having problem trying to associate sop protocol with sopcast-player in Firefox 3.6.3. I can run sopcast-player by itself just fine on Lucid 10.04. I've already added the following via "about:config":

string name: network.protocol-handler.app.sop
string value: sopcast-player


When I tried to open a sopcast link, I get this message from Firefox:

"Firefox doesn't know how to open this address, because the protocol (sop) isn't associated with any program."

Firefox didn't give me dialog box where I can choose application like it used to.

---

### Post by afrodeity on 2010-04-10
Nobody seems to be helping me with my sopcast problem.

So now I found a qt version. I have an early version which can't download the channel guide, running.

I am therefore trying to compile the latest release

I have installed the Qt3-dev files

but get this error:

```

make
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/channel.o channel.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/config.o config.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/playfork.o playfork.cpp
playfork.cpp: In member function &#8216;void PlayFork::onPlayerExit()&#8217;:
playfork.cpp:117: warning: suggest explicit braces to avoid ambiguous &#8216;else&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/loadsave.o loadsave.cpp
loadsave.cpp: In member function &#8216;void LoadSave::saveopenstate()&#8217;:
loadsave.cpp:130: warning: ignoring return value of &#8216;ssize_t write(int, const void*, size_t)&#8217;, declared with attribute warn_unused_result
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/main.o main.cpp
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:47: error: &#8216;srand&#8217; was not declared in this scope
make: *** [.obj/main.o] Error 1

```

---

### Post by flyguy97 on 2010-04-11
> **afrodeity said:**
> Nobody seems to be helping me with my sopcast problem.

So now I found a qt version. I have an early version which can't download the channel guide, running.

I am therefore trying to compile the latest release

I have installed the Qt3-dev files

but get this error:

```

make
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/channel.o channel.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/config.o config.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/playfork.o playfork.cpp
playfork.cpp: In member function ‘void PlayFork::onPlayerExit()’:
playfork.cpp:117: warning: suggest explicit braces to avoid ambiguous ‘else’
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/loadsave.o loadsave.cpp
loadsave.cpp: In member function ‘void LoadSave::saveopenstate()’:
loadsave.cpp:130: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DALSA -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/main.o main.cpp
main.cpp: In function ‘int main(int, char**)’:
main.cpp:47: error: ‘srand’ was not declared in this scope
make: *** [.obj/main.o] Error 1

```

I would be happy to help you with your SopCast Player issues. What version of Ubuntu are you running and what is the output at the terminal when you run sopcast-player?

Cheers,
Jason

---

### Post by flyguy97 on 2010-04-11
> **oobuntoo said:**
> I'm having problem trying to associate sop protocol with sopcast-player in Firefox 3.6.3. I can run sopcast-player by itself just fine on Lucid 10.04. I've already added the following via "about:config":

string name: network.protocol-handler.app.sop
string value: sopcast-player


When I tried to open a sopcast link, I get this message from Firefox:

"Firefox doesn't know how to open this address, because the protocol (sop) isn't associated with any program."

Firefox didn't give me dialog box where I can choose application like it used to.


Please try to uninstall sopcast-player then re-install from the command line. Please post the output.

Cheers,
Jason

---

### Post by afrodeity on 2010-04-11
> **flyguy97 said:**
> I would be happy to help you with your SopCast Player issues. What version of Ubuntu are you running and what is the output at the terminal when you run sopcast-player?

Cheers,
Jason

```

$ sopcast-player
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 1780, in <module>
    pySop = pySopCast()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 368, in __init__
    self.vlc = VLCWidget.VLCWidget(*p)
  File "/usr/share/sopcast-player/lib/VLCWidget.py", line 28, in __init__
    self.player=instance.mediacontrol_new_from_instance()
AttributeError: 'Instance' object has no attribute 'mediacontrol_new_from_instance'

```

This is for the GTK sopcast player, I think it has something to do with VLC 1.1 which has slightly different architecture than earlier VLC. 
First time this happened I got a message about the plugin path. Not sure how to fix it.

---

### Post by flyguy97 on 2010-04-11
> **afrodeity said:**
> ```

$ sopcast-player
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 1780, in <module>
    pySop = pySopCast()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 368, in __init__
    self.vlc = VLCWidget.VLCWidget(*p)
  File "/usr/share/sopcast-player/lib/VLCWidget.py", line 28, in __init__
    self.player=instance.mediacontrol_new_from_instance()
AttributeError: 'Instance' object has no attribute 'mediacontrol_new_from_instance'

```

This is for the GTK sopcast player, I think it has something to do with VLC 1.1 which has slightly different architecture than earlier VLC. 
First time this happened I got a message about the plugin path. Not sure how to fix it.

The problem is the python bindings (used to access vlc) has been updated for version 1.1.x. As of this moment I am unable to figure out how to gracefully deal with two different versions of the bindings (the newest version will only work with vlc 1.1.x while the older bindings are required for anything prior). Be assured that I am working to fix this issue. Would you like to assist me in the troubleshooting?

Cheers,
Jason

---

### Post by flyguy97 on 2010-04-11
All,

The python bindings are currently being updated for vlc 1.1.x. An change in the underlying data structures have forced the bindings team to retool the bindings. The team is currently waiting on the vlc API to stabilise before a release is issued. Sorry for any inconvenience. I will be sure to update SopCast Player as soon as the new bindings are released.

Cheers,
Jason

---

### Post by flyguy97 on 2010-04-11
> **oobuntoo said:**
> I'm having problem trying to associate sop protocol with sopcast-player in Firefox 3.6.3. I can run sopcast-player by itself just fine on Lucid 10.04. I've already added the following via "about:config":

string name: network.protocol-handler.app.sop
string value: sopcast-player


When I tried to open a sopcast link, I get this message from Firefox:

"Firefox doesn't know how to open this address, because the protocol (sop) isn't associated with any program."

Firefox didn't give me dialog box where I can choose application like it used to.

Did you install from my ppa?

---

### Post by frokki on 2010-04-11
> **flyguy97 said:**
> Did you install from my ppa?

I did, and instead of opening a channel, it goes to that endless Connecting -> Retrying channel -loop.
What should I do next/instead?

---

### Post by oobuntoo on 2010-04-11
> **flyguy97 said:**
> Please try to uninstall sopcast-player then re-install from the command line. Please post the output.

Cheers,
Jason

Yes, I installed it from the PPA. I reinstalled and it still doesn't work. Here's the output from reinstall:

```
kwan@sexbomb:~$ sudo apt-get install sopcast-player
[sudo] password for kwan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gconf2 lib32stdc++5 libass4 libavc1394-0 libcddb2 libdca0 libdvbpsi5 libebml0 liblua5.1-0 libmatroska0 libnotify1 libraw1394-11
  libsdl-image1.2 libsexy2 libshout3 libstartup-notification0 libtar libupnp3 libvlc-dev libvlc2 libvlccore-dev libvlccore2
  libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxcb-keysyms1 libxres1 notification-daemon sp-auth vlc vlc-data
  vlc-nox vlc-plugin-pulse
Suggested packages:
  gconf-defaults-service libraw1394-doc python-gnome2 mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  gconf2 lib32stdc++5 libass4 libavc1394-0 libcddb2 libdca0 libdvbpsi5 libebml0 liblua5.1-0 libmatroska0 libnotify1 libraw1394-11
  libsdl-image1.2 libsexy2 libshout3 libstartup-notification0 libtar libupnp3 libvlc-dev libvlc2 libvlccore-dev libvlccore2
  libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxcb-keysyms1 libxres1 notification-daemon sopcast-player sp-auth
  vlc vlc-data vlc-nox vlc-plugin-pulse
0 upgraded, 36 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.5MB/14.7MB of archives.
After this operation, 47.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main gconf2 2.28.1-0ubuntu1 [62.0kB]
Get:2 http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/ lucid/main lib32stdc++5 3.3.6~ppa~lucid2 [182kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libcddb2 1.3.2-0ubuntu1 [51.5kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libdvbpsi5 0.1.6-1 [35.2kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libebml0 0.7.7-3.1 [64.2kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid/main liblua5.1-0 5.1.4-5 [89.5kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libmatroska0 0.8.1-1.1 [206kB]
Get:8 http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/ lucid/main sp-auth 3.2.6~ppa1~lucid7 [345kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid/main libnotify1 0.4.5-1ubuntu3 [21.9kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid/main libraw1394-11 2.0.4-1ubuntu2 [45.5kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libsdl-image1.2 1.2.10-1 [34.2kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ lucid/main libsexy2 0.1.11-2build2 [35.1kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ lucid/main libshout3 2.2.2-5ubuntu1 [40.2kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxcb-atom1 0.3.6-1build1 [10.3kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxcb-aux0 0.3.6-1build1 [8,962B]
Get:16 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxcb-event1 0.3.6-1build1 [9,608B]
Get:17 http://us.archive.ubuntu.com/ubuntu/ lucid/main libstartup-notification0 0.10-1build1 [20.0kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libtar 1.2.11-6 [21.6kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ lucid/universe vlc-data 1.0.5-2ubuntu1 [7,128kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libvlccore2 1.0.5-2ubuntu1 [400kB]                                           
Get:21 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libvlc2 1.0.5-2ubuntu1 [52.5kB]                                              
Get:22 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libvlccore-dev 1.0.5-2ubuntu1 [582kB]                                        
Get:23 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libvlc-dev 1.0.5-2ubuntu1 [76.3kB]                                           
Get:24 http://us.archive.ubuntu.com/ubuntu/ lucid/main libwnck-common 1:2.30.0-0ubuntu1 [19.8kB]                                        
Get:25 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxres1 2:1.0.4-1 [11.5kB]                                                      
Get:26 http://us.archive.ubuntu.com/ubuntu/ lucid/main libwnck22 1:2.30.0-0ubuntu1 [120kB]                                              
Get:27 http://us.archive.ubuntu.com/ubuntu/ lucid/main notification-daemon 0.4.0-2ubuntu2 [61.3kB]                                      
Get:28 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libass4 0.9.9-0ubuntu1 [55.8kB]                                              
Get:29 http://us.archive.ubuntu.com/ubuntu/ lucid/main libavc1394-0 0.5.3-1build4 [22.9kB]                                              
Get:30 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libdca0 0.0.5-3 [109kB]                                                      
Get:31 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libupnp3 1:1.6.6-4 [106kB]                                                   
Get:32 http://us.archive.ubuntu.com/ubuntu/ lucid/universe vlc-nox 1.0.5-2ubuntu1 [2,811kB]                                             
Get:33 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxcb-keysyms1 0.3.6-1build1 [8,390B]                                           
Get:34 http://us.archive.ubuntu.com/ubuntu/ lucid/universe vlc 1.0.5-2ubuntu1 [1,622kB]                                                 
Get:35 http://us.archive.ubuntu.com/ubuntu/ lucid/universe vlc-plugin-pulse 1.0.5-2ubuntu1 [7,194B]                                     
Fetched 14.5MB in 22s (656kB/s)                                                                                                         
Extracting templates from packages: 100%
Selecting previously deselected package lib32stdc++5.
(Reading database ... 133634 files and directories currently installed.)
Unpacking lib32stdc++5 (from .../lib32stdc++5_3.3.6~ppa~lucid2_amd64.deb) ...
Selecting previously deselected package gconf2.
Unpacking gconf2 (from .../gconf2_2.28.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libcddb2.
Unpacking libcddb2 (from .../libcddb2_1.3.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libdvbpsi5.
Unpacking libdvbpsi5 (from .../libdvbpsi5_0.1.6-1_amd64.deb) ...
Selecting previously deselected package libebml0.
Unpacking libebml0 (from .../libebml0_0.7.7-3.1_amd64.deb) ...
Selecting previously deselected package liblua5.1-0.
Unpacking liblua5.1-0 (from .../liblua5.1-0_5.1.4-5_amd64.deb) ...
Selecting previously deselected package libmatroska0.
Unpacking libmatroska0 (from .../libmatroska0_0.8.1-1.1_amd64.deb) ...
Selecting previously deselected package libnotify1.
Unpacking libnotify1 (from .../libnotify1_0.4.5-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libraw1394-11.
Unpacking libraw1394-11 (from .../libraw1394-11_2.0.4-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libsdl-image1.2.
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.10-1_amd64.deb) ...
Selecting previously deselected package libsexy2.
Unpacking libsexy2 (from .../libsexy2_0.1.11-2build2_amd64.deb) ...
Selecting previously deselected package libshout3.
Unpacking libshout3 (from .../libshout3_2.2.2-5ubuntu1_amd64.deb) ...
Selecting previously deselected package libxcb-atom1.
Unpacking libxcb-atom1 (from .../libxcb-atom1_0.3.6-1build1_amd64.deb) ...
Selecting previously deselected package libxcb-aux0.
Unpacking libxcb-aux0 (from .../libxcb-aux0_0.3.6-1build1_amd64.deb) ...
Selecting previously deselected package libxcb-event1.
Unpacking libxcb-event1 (from .../libxcb-event1_0.3.6-1build1_amd64.deb) ...
Selecting previously deselected package libstartup-notification0.
Unpacking libstartup-notification0 (from .../libstartup-notification0_0.10-1build1_amd64.deb) ...
Selecting previously deselected package libtar.
Unpacking libtar (from .../libtar_1.2.11-6_amd64.deb) ...
Selecting previously deselected package vlc-data.
Unpacking vlc-data (from .../vlc-data_1.0.5-2ubuntu1_all.deb) ...
Selecting previously deselected package libvlccore2.
Unpacking libvlccore2 (from .../libvlccore2_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libvlc2.
Unpacking libvlc2 (from .../libvlc2_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libvlccore-dev.
Unpacking libvlccore-dev (from .../libvlccore-dev_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libvlc-dev.
Unpacking libvlc-dev (from .../libvlc-dev_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libwnck-common.
Unpacking libwnck-common (from .../libwnck-common_1%3a2.30.0-0ubuntu1_all.deb) ...
Selecting previously deselected package libxres1.
Unpacking libxres1 (from .../libxres1_2%3a1.0.4-1_amd64.deb) ...
Selecting previously deselected package libwnck22.
Unpacking libwnck22 (from .../libwnck22_1%3a2.30.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package notification-daemon.
Unpacking notification-daemon (from .../notification-daemon_0.4.0-2ubuntu2_amd64.deb) ...
Selecting previously deselected package libass4.
Unpacking libass4 (from .../libass4_0.9.9-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libavc1394-0.
Unpacking libavc1394-0 (from .../libavc1394-0_0.5.3-1build4_amd64.deb) ...
Selecting previously deselected package libdca0.
Unpacking libdca0 (from .../libdca0_0.0.5-3_amd64.deb) ...
Selecting previously deselected package libupnp3.
Unpacking libupnp3 (from .../libupnp3_1%3a1.6.6-4_amd64.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libxcb-keysyms1.
Unpacking libxcb-keysyms1 (from .../libxcb-keysyms1_0.3.6-1build1_amd64.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package vlc-plugin-pulse.
Unpacking vlc-plugin-pulse (from .../vlc-plugin-pulse_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package sp-auth.
Unpacking sp-auth (from .../sp-auth_3.2.6~ppa1~lucid7_amd64.deb) ...
Selecting previously deselected package sopcast-player.
Unpacking sopcast-player (from .../sopcast-player_0.4.0~ppa1~lucid4_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Setting up lib32stdc++5 (3.3.6~ppa~lucid2) ...

Setting up gconf2 (2.28.1-0ubuntu1) ...
update-alternatives: using /usr/bin/gconftool-2 to provide /usr/bin/gconftool (gconftool) in auto mode.

Setting up libcddb2 (1.3.2-0ubuntu1) ...

Setting up libdvbpsi5 (0.1.6-1) ...

Setting up libebml0 (0.7.7-3.1) ...

Setting up liblua5.1-0 (5.1.4-5) ...

Setting up libmatroska0 (0.8.1-1.1) ...

Setting up libnotify1 (0.4.5-1ubuntu3) ...

Setting up libraw1394-11 (2.0.4-1ubuntu2) ...

Setting up libsdl-image1.2 (1.2.10-1) ...

Setting up libsexy2 (0.1.11-2build2) ...

Setting up libshout3 (2.2.2-5ubuntu1) ...

Setting up libxcb-atom1 (0.3.6-1build1) ...

Setting up libxcb-aux0 (0.3.6-1build1) ...

Setting up libxcb-event1 (0.3.6-1build1) ...

Setting up libstartup-notification0 (0.10-1build1) ...

Setting up libtar (1.2.11-6) ...

Setting up vlc-data (1.0.5-2ubuntu1) ...
Setting up libvlccore2 (1.0.5-2ubuntu1) ...

Setting up libvlc2 (1.0.5-2ubuntu1) ...

Setting up libvlccore-dev (1.0.5-2ubuntu1) ...
Setting up libvlc-dev (1.0.5-2ubuntu1) ...
Setting up libwnck-common (1:2.30.0-0ubuntu1) ...
Setting up libxres1 (2:1.0.4-1) ...

Setting up libwnck22 (1:2.30.0-0ubuntu1) ...

Setting up notification-daemon (0.4.0-2ubuntu2) ...
notification-daemon: no process found

Setting up libass4 (0.9.9-0ubuntu1) ...

Setting up libavc1394-0 (0.5.3-1build4) ...

Setting up libdca0 (0.0.5-3) ...

Setting up libupnp3 (1:1.6.6-4) ...

Setting up vlc-nox (1.0.5-2ubuntu1) ...
Setting up libxcb-keysyms1 (0.3.6-1build1) ...

Setting up vlc (1.0.5-2ubuntu1) ...

Setting up vlc-plugin-pulse (1.0.5-2ubuntu1) ...
Setting up sp-auth (3.2.6~ppa1~lucid7) ...
Setting up sopcast-player (0.4.0~ppa1~lucid4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
kwan@sexbomb:~$
```

---

### Post by flyguy97 on 2010-04-12
> **oobuntoo said:**
> Yes, I installed it from the PPA. I reinstalled and it still doesn't work. Here's the output from reinstall:

```
kwan@sexbomb:~$ sudo apt-get install sopcast-player
[sudo] password for kwan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gconf2 lib32stdc++5 libass4 libavc1394-0 libcddb2 libdca0 libdvbpsi5 libebml0 liblua5.1-0 libmatroska0 libnotify1 libraw1394-11
  libsdl-image1.2 libsexy2 libshout3 libstartup-notification0 libtar libupnp3 libvlc-dev libvlc2 libvlccore-dev libvlccore2
  libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxcb-keysyms1 libxres1 notification-daemon sp-auth vlc vlc-data
  vlc-nox vlc-plugin-pulse
Suggested packages:
  gconf-defaults-service libraw1394-doc python-gnome2 mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  gconf2 lib32stdc++5 libass4 libavc1394-0 libcddb2 libdca0 libdvbpsi5 libebml0 liblua5.1-0 libmatroska0 libnotify1 libraw1394-11
  libsdl-image1.2 libsexy2 libshout3 libstartup-notification0 libtar libupnp3 libvlc-dev libvlc2 libvlccore-dev libvlccore2
  libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxcb-keysyms1 libxres1 notification-daemon sopcast-player sp-auth
  vlc vlc-data vlc-nox vlc-plugin-pulse
0 upgraded, 36 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.5MB/14.7MB of archives.
After this operation, 47.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main gconf2 2.28.1-0ubuntu1 [62.0kB]
Get:2 http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/ lucid/main lib32stdc++5 3.3.6~ppa~lucid2 [182kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libcddb2 1.3.2-0ubuntu1 [51.5kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libdvbpsi5 0.1.6-1 [35.2kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libebml0 0.7.7-3.1 [64.2kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid/main liblua5.1-0 5.1.4-5 [89.5kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libmatroska0 0.8.1-1.1 [206kB]
Get:8 http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/ lucid/main sp-auth 3.2.6~ppa1~lucid7 [345kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid/main libnotify1 0.4.5-1ubuntu3 [21.9kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid/main libraw1394-11 2.0.4-1ubuntu2 [45.5kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libsdl-image1.2 1.2.10-1 [34.2kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ lucid/main libsexy2 0.1.11-2build2 [35.1kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ lucid/main libshout3 2.2.2-5ubuntu1 [40.2kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxcb-atom1 0.3.6-1build1 [10.3kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxcb-aux0 0.3.6-1build1 [8,962B]
Get:16 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxcb-event1 0.3.6-1build1 [9,608B]
Get:17 http://us.archive.ubuntu.com/ubuntu/ lucid/main libstartup-notification0 0.10-1build1 [20.0kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libtar 1.2.11-6 [21.6kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ lucid/universe vlc-data 1.0.5-2ubuntu1 [7,128kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libvlccore2 1.0.5-2ubuntu1 [400kB]                                           
Get:21 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libvlc2 1.0.5-2ubuntu1 [52.5kB]                                              
Get:22 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libvlccore-dev 1.0.5-2ubuntu1 [582kB]                                        
Get:23 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libvlc-dev 1.0.5-2ubuntu1 [76.3kB]                                           
Get:24 http://us.archive.ubuntu.com/ubuntu/ lucid/main libwnck-common 1:2.30.0-0ubuntu1 [19.8kB]                                        
Get:25 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxres1 2:1.0.4-1 [11.5kB]                                                      
Get:26 http://us.archive.ubuntu.com/ubuntu/ lucid/main libwnck22 1:2.30.0-0ubuntu1 [120kB]                                              
Get:27 http://us.archive.ubuntu.com/ubuntu/ lucid/main notification-daemon 0.4.0-2ubuntu2 [61.3kB]                                      
Get:28 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libass4 0.9.9-0ubuntu1 [55.8kB]                                              
Get:29 http://us.archive.ubuntu.com/ubuntu/ lucid/main libavc1394-0 0.5.3-1build4 [22.9kB]                                              
Get:30 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libdca0 0.0.5-3 [109kB]                                                      
Get:31 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libupnp3 1:1.6.6-4 [106kB]                                                   
Get:32 http://us.archive.ubuntu.com/ubuntu/ lucid/universe vlc-nox 1.0.5-2ubuntu1 [2,811kB]                                             
Get:33 http://us.archive.ubuntu.com/ubuntu/ lucid/main libxcb-keysyms1 0.3.6-1build1 [8,390B]                                           
Get:34 http://us.archive.ubuntu.com/ubuntu/ lucid/universe vlc 1.0.5-2ubuntu1 [1,622kB]                                                 
Get:35 http://us.archive.ubuntu.com/ubuntu/ lucid/universe vlc-plugin-pulse 1.0.5-2ubuntu1 [7,194B]                                     
Fetched 14.5MB in 22s (656kB/s)                                                                                                         
Extracting templates from packages: 100%
Selecting previously deselected package lib32stdc++5.
(Reading database ... 133634 files and directories currently installed.)
Unpacking lib32stdc++5 (from .../lib32stdc++5_3.3.6~ppa~lucid2_amd64.deb) ...
Selecting previously deselected package gconf2.
Unpacking gconf2 (from .../gconf2_2.28.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libcddb2.
Unpacking libcddb2 (from .../libcddb2_1.3.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libdvbpsi5.
Unpacking libdvbpsi5 (from .../libdvbpsi5_0.1.6-1_amd64.deb) ...
Selecting previously deselected package libebml0.
Unpacking libebml0 (from .../libebml0_0.7.7-3.1_amd64.deb) ...
Selecting previously deselected package liblua5.1-0.
Unpacking liblua5.1-0 (from .../liblua5.1-0_5.1.4-5_amd64.deb) ...
Selecting previously deselected package libmatroska0.
Unpacking libmatroska0 (from .../libmatroska0_0.8.1-1.1_amd64.deb) ...
Selecting previously deselected package libnotify1.
Unpacking libnotify1 (from .../libnotify1_0.4.5-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libraw1394-11.
Unpacking libraw1394-11 (from .../libraw1394-11_2.0.4-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libsdl-image1.2.
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.10-1_amd64.deb) ...
Selecting previously deselected package libsexy2.
Unpacking libsexy2 (from .../libsexy2_0.1.11-2build2_amd64.deb) ...
Selecting previously deselected package libshout3.
Unpacking libshout3 (from .../libshout3_2.2.2-5ubuntu1_amd64.deb) ...
Selecting previously deselected package libxcb-atom1.
Unpacking libxcb-atom1 (from .../libxcb-atom1_0.3.6-1build1_amd64.deb) ...
Selecting previously deselected package libxcb-aux0.
Unpacking libxcb-aux0 (from .../libxcb-aux0_0.3.6-1build1_amd64.deb) ...
Selecting previously deselected package libxcb-event1.
Unpacking libxcb-event1 (from .../libxcb-event1_0.3.6-1build1_amd64.deb) ...
Selecting previously deselected package libstartup-notification0.
Unpacking libstartup-notification0 (from .../libstartup-notification0_0.10-1build1_amd64.deb) ...
Selecting previously deselected package libtar.
Unpacking libtar (from .../libtar_1.2.11-6_amd64.deb) ...
Selecting previously deselected package vlc-data.
Unpacking vlc-data (from .../vlc-data_1.0.5-2ubuntu1_all.deb) ...
Selecting previously deselected package libvlccore2.
Unpacking libvlccore2 (from .../libvlccore2_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libvlc2.
Unpacking libvlc2 (from .../libvlc2_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libvlccore-dev.
Unpacking libvlccore-dev (from .../libvlccore-dev_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libvlc-dev.
Unpacking libvlc-dev (from .../libvlc-dev_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libwnck-common.
Unpacking libwnck-common (from .../libwnck-common_1%3a2.30.0-0ubuntu1_all.deb) ...
Selecting previously deselected package libxres1.
Unpacking libxres1 (from .../libxres1_2%3a1.0.4-1_amd64.deb) ...
Selecting previously deselected package libwnck22.
Unpacking libwnck22 (from .../libwnck22_1%3a2.30.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package notification-daemon.
Unpacking notification-daemon (from .../notification-daemon_0.4.0-2ubuntu2_amd64.deb) ...
Selecting previously deselected package libass4.
Unpacking libass4 (from .../libass4_0.9.9-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libavc1394-0.
Unpacking libavc1394-0 (from .../libavc1394-0_0.5.3-1build4_amd64.deb) ...
Selecting previously deselected package libdca0.
Unpacking libdca0 (from .../libdca0_0.0.5-3_amd64.deb) ...
Selecting previously deselected package libupnp3.
Unpacking libupnp3 (from .../libupnp3_1%3a1.6.6-4_amd64.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libxcb-keysyms1.
Unpacking libxcb-keysyms1 (from .../libxcb-keysyms1_0.3.6-1build1_amd64.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package vlc-plugin-pulse.
Unpacking vlc-plugin-pulse (from .../vlc-plugin-pulse_1.0.5-2ubuntu1_amd64.deb) ...
Selecting previously deselected package sp-auth.
Unpacking sp-auth (from .../sp-auth_3.2.6~ppa1~lucid7_amd64.deb) ...
Selecting previously deselected package sopcast-player.
Unpacking sopcast-player (from .../sopcast-player_0.4.0~ppa1~lucid4_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Setting up lib32stdc++5 (3.3.6~ppa~lucid2) ...

Setting up gconf2 (2.28.1-0ubuntu1) ...
update-alternatives: using /usr/bin/gconftool-2 to provide /usr/bin/gconftool (gconftool) in auto mode.

Setting up libcddb2 (1.3.2-0ubuntu1) ...

Setting up libdvbpsi5 (0.1.6-1) ...

Setting up libebml0 (0.7.7-3.1) ...

Setting up liblua5.1-0 (5.1.4-5) ...

Setting up libmatroska0 (0.8.1-1.1) ...

Setting up libnotify1 (0.4.5-1ubuntu3) ...

Setting up libraw1394-11 (2.0.4-1ubuntu2) ...

Setting up libsdl-image1.2 (1.2.10-1) ...

Setting up libsexy2 (0.1.11-2build2) ...

Setting up libshout3 (2.2.2-5ubuntu1) ...

Setting up libxcb-atom1 (0.3.6-1build1) ...

Setting up libxcb-aux0 (0.3.6-1build1) ...

Setting up libxcb-event1 (0.3.6-1build1) ...

Setting up libstartup-notification0 (0.10-1build1) ...

Setting up libtar (1.2.11-6) ...

Setting up vlc-data (1.0.5-2ubuntu1) ...
Setting up libvlccore2 (1.0.5-2ubuntu1) ...

Setting up libvlc2 (1.0.5-2ubuntu1) ...

Setting up libvlccore-dev (1.0.5-2ubuntu1) ...
Setting up libvlc-dev (1.0.5-2ubuntu1) ...
Setting up libwnck-common (1:2.30.0-0ubuntu1) ...
Setting up libxres1 (2:1.0.4-1) ...

Setting up libwnck22 (1:2.30.0-0ubuntu1) ...

Setting up notification-daemon (0.4.0-2ubuntu2) ...
notification-daemon: no process found

Setting up libass4 (0.9.9-0ubuntu1) ...

Setting up libavc1394-0 (0.5.3-1build4) ...

Setting up libdca0 (0.0.5-3) ...

Setting up libupnp3 (1:1.6.6-4) ...

Setting up vlc-nox (1.0.5-2ubuntu1) ...
Setting up libxcb-keysyms1 (0.3.6-1build1) ...

Setting up vlc (1.0.5-2ubuntu1) ...

Setting up vlc-plugin-pulse (1.0.5-2ubuntu1) ...
Setting up sp-auth (3.2.6~ppa1~lucid7) ...
Setting up sopcast-player (0.4.0~ppa1~lucid4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
kwan@sexbomb:~$
```

It sounds like something may have happened to gconf. gconf is where associations are kept. Try deleting your gconf (this WILL erase all user settings for current programs) and then through synaptic choose to fully remove sopcast-player and then reinstall. I have the same setup (10.04 with FF 3.6.3) and mine worked out of the box. Let me know how this works for you.

Regards,
Jason

---

### Post by afrodeity on 2010-04-12
> **flyguy97 said:**
> The problem is the python bindings (used to access vlc) has been updated for version 1.1.x. As of this moment I am unable to figure out how to gracefully deal with two different versions of the bindings (the newest version will only work with vlc 1.1.x while the older bindings are required for anything prior). Be assured that I am working to fix this issue. Would you like to assist me in the troubleshooting?

Cheers,
Jason

Aha, the python bindings. Perhaps Sopcast needs to be branched for the post-VLC-1.1x expansion?

Thanks Jason, I can assist as much as possible. Tell me what you need me to do. I am a bit of a novice as far as python is concerned, your app rocks (when it works).

;)

---

### Post by oobuntoo on 2010-04-12
> **flyguy97 said:**
> It sounds like something may have happened to gconf. gconf is where associations are kept. Try deleting your gconf (this WILL erase all user settings for current programs) and then through synaptic choose to fully remove sopcast-player and then reinstall. I have the same setup (10.04 with FF 3.6.3) and mine worked out of the box. Let me know how this works for you.

Regards,
Jason

I'm using KDE (Kubuntu) and my .gconf folder is empty. Maybe this is the reason, but it worked before under 9.10.

---

### Post by zordo on 2010-04-25
Having trouble installing sp-auth. Synaptic tells me that its dependant  on   libstdc++5 , and that is unistallable for me(i have libstdc++6). Im running 10.04.

---

### Post by howefield on 2010-04-25
> **zordo said:**
> Having trouble installing sp-auth.

Have you added the PPA for Lucid ?

---

### Post by zordo on 2010-04-25
> **howefield said:**
> Have you added the PPA for Lucid ?
Well the sp-auth  package's latest version in synaptic is   3.2.6~ppa~lucid7.
I used [these]("http://code.google.com/p/sopcast-player/wiki/Installation") instructions.

im missing   lib32stdc++5.
Is it a different ppa for lucid?
Synaptic shows   LP-PPA-jason-scheunemann/lucid   as one source.

---

### Post by howefield on 2010-04-26
I manually added the following to Synaptic, not sure sure if would make a difference but sopcast-player installed for me perfectly with all it's dependancies.


```
http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu lucid main
```

---

### Post by greenjumper on 2010-04-30
I got this error when trying to install on Lucid:

> The following packages have unmet dependencies:
  sopcast-player: Depends: sp-auth (>= 3.0.1) but it is not going to be installed
E: Broken packages


Anyone got any ideas?

---

### Post by 135798642 on 2010-05-01
here [http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download)
then install sp-auth,sopcast-player ... :)

---

### Post by greenjumper on 2010-05-02
> **135798642 said:**
> here [http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download)
then install sp-auth,sopcast-player ... :)

Thank you very much! That worked a treat!

---

### Post by beegary on 2010-05-02
> **greenjumper said:**
> Thank you very much! That worked a treat!

+1 thank you very much.My life is incomplete without sopcast!!!!

---

### Post by afrodeity on 2010-05-02
I installed sopcast on my laptop which has a fresh lucid install, its working but no channels 

This link doesn't seem to download anything [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)

are there any other channel guide links for sopplayer?

---

### Post by afrodeity on 2010-05-02
Wondering if there is an update-alternatives or zero-install solution to having more than one VLC version on my desktop system.:)

[http://www.debian-administration.org/articles/91](http://www.debian-administration.org/articles/91)

[http://0install.net/injector-using.html](http://0install.net/injector-using.html)

---

### Post by joanmunoz on 2010-05-05
Hi!

I'm trying to open an external player (VLC-Desktop), but nothing happens when the buffer is full and it is supposed the image would be displayed. Any help on this issue?

My specs:

Linux joan-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
Sopcast Player 0.4.0
VLC 1.0.6 Goldeneye

Thx!!

Joan

---

### Post by Bo Rosén on 2010-05-08
> **flyguy97 said:**
> Try deleting your gconf (this WILL erase all user settings for current programs) and then through synaptic choose to fully remove sopcast-player and then reinstall.


I have the same problem with links in firefox not starting sopcast-player. I installed it via the repos.

When it didn't work (it works from the Gnome Menu) I tried purging sopcast-player, renaming .gconf and reinstalling. 
No luck.
I'm on a (relatively) clean Lucid install.

---

### Post by SolitaryMan1941 on 2010-05-09
I'm having a specific issue with the SopCast Player. One channel in particular does not have sound, thought the video is great. All of the other channels I can get up and running have both sound and video. I've run this specific channel (NDSportsTalk) on a computer with Windows 7 64-bit and it has sound and video so I know the problem is on my end. My HTPC runs Ubuntu Lucid 32-bit (the only OS installed at this time) and I'd prefer to watch TV in the living room. Any ideas?

If I need to reinstall my OS as Lucid 64-bit I can. My system has enough power to upgrade.

---

### Post by matzi11a on 2010-05-11
I was having problem with sop://whatever not working in firefox 3.6 on 10.04 (it was a dist-upgrade from 9.10 fwiw), sopcast-player working fine from menu and cmd line.

editing firefox about:config does not work anymore!!

this solved my issue:
gconftool-2 -t string -s /desktop/gnome/url-handlers/sop/command "/usr/bin/sopcast-player %s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/sop/needs_terminal false
gconftool-2 -t bool -s /desktop/gnome/url-handlers/sop/enabled true

ref: [http://forum.ubuntu-it.org/index.php?topic=380533.msg2954371;topicseen](http://forum.ubuntu-it.org/index.php?topic=380533.msg2954371;topicseen)


regards.:guitar:

---

### Post by Bo Rosén on 2010-05-12
> **matzi11a said:**
> 
gconftool-2 -t string -s /desktop/gnome/url-handlers/sop/command "/usr/bin/sopcast-player %s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/sop/needs_terminal false
gconftool-2 -t bool -s /desktop/gnome/url-handlers/sop/enabled true


Brilliant! Works a treat, thanks.

---

### Post by Operan on 2010-05-17
> **matzi11a said:**
> I was having problem with sop://whatever not working in firefox 3.6 on 10.04 (it was a dist-upgrade from 9.10 fwiw), sopcast-player working fine from menu and cmd line.

editing firefox about:config does not work anymore!!

this solved my issue:
gconftool-2 -t string -s /desktop/gnome/url-handlers/sop/command "/usr/bin/sopcast-player %s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/sop/needs_terminal false
gconftool-2 -t bool -s /desktop/gnome/url-handlers/sop/enabled true

ref: [http://forum.ubuntu-it.org/index.php?topic=380533.msg2954371;topicseen](http://forum.ubuntu-it.org/index.php?topic=380533.msg2954371;topicseen)


regards.:guitar:

It doesn't work in Kubuntu 10.04 !

---

### Post by tipdrinker on 2010-05-25
Hi I have linux mint 9 installed. I tried to install the deb package and got this error message...

Error: Dependency is not satisfiable: ia32-libs|lib32stdc++5

how do i sort it out. Was hoping to watch the ireland paraguay match this evening on it.:(

---

### Post by tsubaki on 2010-05-25
THX! works grate

---

### Post by tipdrinker on 2010-05-25
had a little more progress but still stuck. Heres what the terminal threw up for me!

kevin@kevin-desktop ~ $ sudo apt-get install sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sopcast-player: Depends: sp-auth (>= 3.0.1) but it is not going to be installed
E: Broken packages

**So i tried this:**

kevin@kevin-desktop ~ $ sudo apt-get install sp-auth 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sp-auth: Depends: libstdc++5 but it is not installable
E: Broken packages

**And tried this**

kevin@kevin-desktop ~ $ sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate
kevin@kevin-desktop ~ $

---

### Post by suli8 on 2010-06-10
hi 
i have the sopcast player that stopped working, and i need your help
it worked good before ... i dont know wts the problem now
when i run it nothing happens..
so i ran it from the terminal and thats what i get


suliman@suliman-laptop:~$ sopcast-player
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 1783, in  <module>
    pySop = pySopCast()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 371, in  __init__
    self.vlc = VLCWidget.VLCWidget(*p)
  File "/usr/share/sopcast-player/lib/VLCWidget.py", line 28, in  __init__
    self.player=instance.mediacontrol_new_from_instanc  e()
AttributeError: 'Instance' object has no attribute  'mediacontrol_new_from_instance'
suliman@suliman-laptop:~$

---

### Post by suli8 on 2010-06-10
i'm sorry i missed the post several pages ago!
i dont remember upgrading the vlc though.... but its in fact 1.1.0 rc the luggage

is there a way to go back to previous version of vlc and get sopcast working?
or i must wait until the update?

thx

---

### Post by suli8 on 2010-06-11
ok, i disabled the 3rd party ppa for vlc
reinstalled the 1.0.6 version
reinstalled sopcast

and problem solved!!
:razz::razz::razz:

---

### Post by afrodeity on 2010-06-11
If you like me and have VLC 1.1.0 rc The Luggage (It keeps getting installed, and haven't figured out from which third party ppa) then try these:

[http://code.google.com/p/gsopcast/](http://code.google.com/p/gsopcast/) 
GTK version of sopcast, has no problem with VLC

[http://code.google.com/p/qsopcast/](http://code.google.com/p/qsopcast/)  \
QT version of sopcast, has no problem with VLC

Both are a little outdated, it appears there has been more development in the main sopcast-player in this topic.

Both have difficulty with downloading the menu, but you can manually choose.

[http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)
[http://www.sopcast.cn/gchlxml](http://www.sopcast.cn/gchlxml) 
[http://channel.sopcast.com/gchlxml](http://channel.sopcast.com/gchlxml)

The only channels which I can watch with my384kb line are the mobile ones. Wish there were a lot more. Please think of those in the third world with low-bandwidth.

Also English subtitles for some of the Chinese Channels would be excellent. Wondering if there is a way to get the subtitles from opensubtitle.org or somewhere else and watch live? Probably wishful thinking.

This is a great project, wish it would update the python bindings so that no VLC conflicts.

:)

---

### Post by ginobe on 2010-06-11
Tipdrinker. i'm a total noob when it comes to linux but i think i found your solution as i had the same problem as you did when installing sopcast-player. it appears that the libstdc++ package is not included in the ubuntu repositories so you have to download it and install it manually. [http://ftp.de.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb ]("http://ftp.de.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb")
once installed, open terminal and run.
sudo apt-get install sopcast-player sp-auth

this worked for me. hope it helps. enjoy. :)

---

### Post by serpfra on 2010-06-13
Hi 
I have SopCast Player 0.4.0 on Ubuntu 10.04 and is working great.
But I'd like to know how can I remove some Bookmarks?
Please help.
T Y

---

### Post by Zunhs on 2010-07-30
Hi,

I have Linux Helena and got the following problem when running 
"sudo apt-get update && sudo apt-get install sopcast-player"

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) helena/main Packages                              
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [1,384B]                   
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) helena/main Packages                              
  404  Not Found
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Packages                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) helena/main Packages                              
  404  Not Found
Fetched 75.1kB in 0s (116kB/s)
W: Failed to fetch [http://ppa.launchpad.net/jcfp/ppa/ubuntu/dists/helena/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/jcfp/ppa/ubuntu/dists/helena/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/helena/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/helena/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Is it because it is 64 bit os or have I done something else wrong? I can watch a sopcast stream in Firefox if I run "./sp-sc-auth sop://broker.sopcast.com:3912/6001 3908 8908 > /dev/null &" in my sp-auth folder and then open [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf) in Firefox.

Regards
~ Z


Edit: Suddenly "sudo apt-get install sopcast-player" worked. I think the second part (after &&) was aborted because of the above error.

sudo apt-get install sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sopcast-player is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 252 not upgraded.

The gui works now and it looks great. =)


2nd edit:

I also got Firefox to open sop-links after finding this guide:
[http://maketecheasier.com/install-sopcast-in-ubuntu/2010/06/10](http://maketecheasier.com/install-sopcast-in-ubuntu/2010/06/10)

network.protocol-handler.expose-all    <  needed to be toggled to False to ask location of sopcast-player the first time
Set location to /usr/bin/sopcast-player after you click a sop-link
Then toggle back the value in network.protocol-handler.expose-all to True

Now sopcast-player opens up a new player everytime I click a sop-link. *smiles happily*

---

### Post by DeanoCYM on 2010-09-09
Thanks for the great work on this project, I didn't miss an Arsenal game all of last season :)

Any plans to put up a new package for maverick?

Using the Lucid files in maverick doesn't work, something about a conflict with a package called ai32-libs?

---

### Post by vagrale13 on 2010-09-14
Same problem with [post #413]("http://ubuntuforums.org/showpost.php?p=9442961&postcount=413") in *Maverick beta*
Here the output
```
:~$ sopcast-player
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 1783, in <module>
    pySop = pySopCast()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 371, in __init__
    self.vlc = VLCWidget.VLCWidget(*p)
  File "/usr/share/sopcast-player/lib/VLCWidget.py", line 28, in __init__
    self.player=instance.mediacontrol_new_from_instance()
AttributeError: 'Instance' object has no attribute 'mediacontrol_new_from_instance'

```and *VLC media player 1.1.4 The Luggage*

---

### Post by ilabor on 2010-09-14
Hey I just released a fix for sopcast-player with VLC 1.1.4 installed

check [http://code.google.com/p/sopcast-player/issues/detail?id=43#c5](http://code.google.com/p/sopcast-player/issues/detail?id=43#c5)

-mike

---

### Post by vagrale13 on 2010-09-15
> **ilabor said:**
> Hey I just released a fix for sopcast-player with VLC 1.1.4 installed

check [http://code.google.com/p/sopcast-player/issues/detail?id=43#c5](http://code.google.com/p/sopcast-player/issues/detail?id=43#c5)

-mike
Yes works fine in [I]Maverick beta. 
[/I]Thanks[I] :KS
[/I]

---

### Post by wkhasintha on 2010-09-15
Both player and channel guide on the same window

---

### Post by clive littlewood on 2010-09-15
Hi Vagrale13

You have sopcast player working in maverick beta ??

Could you please tell me how you achieved this.

I have used the player in other releases but cannot seem to get this from any PPA.

Any help would be appreciated  :D

Clive

---

### Post by vagrale13 on 2010-09-15
> **clive littlewood said:**
> Hi Vagrale13

You have sopcast player working in maverick beta ??

Could you please tell me how you achieved this.

I have used the player in other releases but cannot seem to get this from any PPA.

Any help would be appreciated  :D

Clive
Download and install the .deb packages 
[sp-auth - 3.2.6~ppa1~lucid7]("https://launchpad.net/%7Ejason-scheunemann/+archive/ppa/+sourcepub/937538/+listing-archive-extra") & [sopcast-player - 0.4.0~ppa1~lucid4]("https://launchpad.net/%7Ejason-scheunemann/+archive/ppa/+sourcepub/1074616/+listing-archive-extra")
from here: [https://launchpad.net/~jason-scheunemann/+archive/ppa/+packages]("https://launchpad.net/%7Ejason-scheunemann/+archive/ppa/+packages")

Then download the .zip file **sopcast-player_vlc1.1x-fix.zip**   
from here [http://code.google.com/p/sopcast-player/issues/detail?id=43#c6](http://code.google.com/p/sopcast-player/issues/detail?id=43#c6)[FONT=monospace]
[/FONT]extracted file - and two archives **vlc.py** & **VLCWidget.py**
replace them to the folder */usr/share/sopcast-player/lib*
use command
```
sudo nautilus
```or run these commands 
```
cd /path/to_the_extrack_folder/with_archives
sudo mv vlc.py /usr/share/sopcast-player/lib
sudo mv VLCWidget.py /usr/share/sopcast-player/lib
```Then try to open **sopcast-player** from *menu*, and must be works! :KS

Then, if you want to play fullscreen go to sopcast-player menu - Edit - preferences - and use command **vlc**
like this
[IMG]http://img828.imageshack.us/img828/3170/screenshotde.png[/IMG]

and after that, must be works in Maverick! :)

---

### Post by realzippy on 2010-09-15
ELLA vagrale13!

..things might have changed (?),but remember wracking whole filesystem once by running:
sudo dolphin instead of **gk**sudo dolphin.If in doubt use

gksudo nautilus

---

### Post by howefield on 2010-09-15
> **vagrale13 said:**
> ```
sudo nautilus
```

Indeed, seems to work perfectly, however if you want to invoke nautilus with elevated rights use...

```
gksudo nautilus
```

---

### Post by clive littlewood on 2010-09-15
Hi Vagrale13

Thanks for the info.

When I try and run the sp=auth deb I get the following dependency error  " ia32-libs|lib32stdc++5 "

Do you know of a deb for this ???

Thanks

Clive

---

### Post by ilabor on 2010-09-15
hey clive,

STFW ;)
[http://www.webupd8.org/2010/05/install-linux-sopcast-player-040-in.html](http://www.webupd8.org/2010/05/install-linux-sopcast-player-040-in.html)

---

### Post by vagrale13 on 2010-09-15
> **clive littlewood said:**
> When I try and run the sp=auth deb I get the following dependency error  " ia32-libs|lib32stdc++5 "
Install **libstdc++5** from *synaptic*, and try to install sopcast-player again! 
If you want it for *.deb* here [http://packages.ubuntu.com/maverick/libstdc++5](http://packages.ubuntu.com/maverick/libstdc++5)
Then, i think must be work. 

**@ilabor**
I think these PPA doesn' t work with Maverick! :popcorn:

---

### Post by clive littlewood on 2010-09-15
Hi All

Thanks everyone for the help.

Everything now working OK   :D

What a fantastic forum this is.

Thanks again

Clive

---

### Post by clive littlewood on 2010-09-16
Whoops

Spoke too soon !!!!!

Now getting broken packages message in synaptic and the only way to get rid is to uninstall.

Have tried to do the complete install again but same result.

I think the problem is that I,m installing the lucid PPA on a Maverick system.

Will wait for the proper maverick PPA to arrive methinks.

I have sopcast player working on another box so that is not a problem.

Clive

---

### Post by max69 on 2010-09-26
Works perfectly ! Thanks !!! (had to downgrade the ia32 libs for skype anyway)

---

### Post by 0N3 on 2010-09-26
Works perfectly for me on Ubuntu Maverick Meerkat 10.10 x86_64 using VLC Media Player version 1.1.4 one tiny problem is it freezes every 5 seconds but only for bare fraction of a second otherwise working perfectly for me thanks for great software.

---

### Post by 0N3 on 2010-09-26
I had to completely remove ia32 and lib32stdc++5 and install older versions and also theres a fix for VLC versions 1.0.0 and higher for this to work. I have all the files i needed to install this but dunno where I can upload them if anybody wanted them for 64bit.

---

### Post by wkhasintha on 2010-09-26
Gotta try this one.

---

### Post by realzippy on 2010-10-12
Hallo Jason,
may I ask if there will be a sopcast player for Maverick in your ppa?
Just asking cause I like to include it in my Maverick-post-install script;
no problem to install the lucid-debs manually.
Thank you again for your work!

---

### Post by Mdi3 on 2010-10-12
error, sorry

---

### Post by Mdi3 on 2010-10-12
Hi everybody,

I'm posting something on this topic because despite all my efforts, i still can't use Sopcast. 

I've been trying to install it for more than 3 months now. Over this period of time, i've done many MANY tutorials. I've uninstalled Sopcast player dozens of times, installed lot of stuff, but still can't get it to work. 

At the moment, i can actually launch Sopcast player. But it won't load any channels. Wether i use one of the "basic" channels there is in the software (like CCTV-5) or try some links i know are online, it doesn't give me anything. 

What i get is "Connecting", and "Trying the canal again" that's it (actually it's in spanish : "Conectando" and "Reintentando canal") 

At this point i just don't know what to do. Do i have a problem with my ports ? If so, how could i solve it ? 


I'll hope you'll be able to help me because after 3 months i'm starting to get lose definitely my hope. 

Thanks a ton !

---

### Post by realzippy on 2010-10-12
@Mdi3
...this used to happen to me back in the karmic days;after reinstalling all related packages and config files it worked-no idea what was causing this issue.
Or have you set "static" ports?

---

### Post by Mdi3 on 2010-10-12
I haven't set static ports, no. 

To be honest , you pretty much crush me with your answer :p , cause I feel like i have already done what you advise me to do , like 50 times :p 
So i was really hoping to have another answer lol. 

Couldn't something else be the problem ??

---

### Post by realzippy on 2010-10-12
If you start in terminal,any error output?
E.g.

```
sopcast-player sop://broker.sopcast.com:3912/6002
```

(which is soccer spain vs scotland,CCTV5,MET now 21.00-c.23.00)

---

### Post by akaAndrew on 2010-10-16
> **Mdi3 said:**
> What i get is "Connecting", and "Trying the canal again" that's it (actually it's in spanish : "Conectando" and "Reintentando canal")

Pretty much the same thing here; 'connecting', 'retrying'.... which ever channel I chose. Is there some firewall related issues or something? Ports on my router that ought be opened up? (Forgive me, I don't really understand these things!)

---

### Post by DeanoCYM on 2010-10-17
Adding the ppa and installing sopcast-player breaks apt for me (in maverick using the lucid .debs), I have to manually locate and rm the packages and the ppa  and 'apt-get -f install' to get my package manager working again. When I'm back at home I will do it again and post the errors here.

Rhys

---

### Post by realzippy on 2010-10-17
> **DeanoCYM said:**
> Adding the ppa and installing sopcast-player breaks apt for me (in maverick using the lucid .debs), I have to manually locate and rm the packages and the ppa  and 'apt-get -f install' to get my package manager working again. When I'm back at home I will do it again and post the errors here.

Rhys

???adding the ppa in maverick should not break anything;here everything is fine (after changing "maverick" to "lucid" in software sources).
Need to add the libs as described in post # 422 to make sopcast work.

---

### Post by nadavbbu on 2010-10-17
That's the messege that I've got when I tried to install Sopcast in Ubuntu 10.10 through the teminal:
"Failed to fetch [http://ppa.launchpad.net/jason-scheu...rce/Sources.gz](http://ppa.launchpad.net/jason-scheu...rce/Sources.gz) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/jason-scheu...86/Packages.gz](http://ppa.launchpad.net/jason-scheu...86/Packages.gz) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramrober...rce/Sources.gz](http://ppa.launchpad.net/ferramrober...rce/Sources.gz) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramrober...86/Packages.gz](http://ppa.launchpad.net/ferramrober...86/Packages.gz) 404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead."

All help will be appreciated.

---

### Post by realzippy on 2010-10-17
> **nadavbbu said:**
> That's the messege that I've got when I tried to install Sopcast in Ubuntu 10.10 through the teminal:
"Failed to fetch [http://ppa.launchpad.net/jason-scheu...rce/Sources.gz](http://ppa.launchpad.net/jason-scheu...rce/Sources.gz) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/jason-scheu...86/Packages.gz](http://ppa.launchpad.net/jason-scheu...86/Packages.gz) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramrober...rce/Sources.gz](http://ppa.launchpad.net/ferramrober...rce/Sources.gz) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramrober...86/Packages.gz](http://ppa.launchpad.net/ferramrober...86/Packages.gz) 404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead."

All help will be appreciated.

Welcome to the forum.
Open from panel
System/Administration/SoftwareSources/OtherSoftware
rightclick each jasonscheunemann line (2),hit "edit",
change "Distribution: maverick"
to "Distribution: lucid".
"reload" software sources.
After this install sopcast-player,do not forget fix (post [#422]("http://ubuntuforums.org/showpost.php?p=9847168&postcount=422")),otherwise it will not start.

---

### Post by DeanoCYM on 2010-10-18
> **realzippy said:**
> ???adding the ppa in maverick should not break anything;here everything is fine (after changing "maverick" to "lucid" in software sources).
Need to add the libs as described in post # 422 to make sopcast work.
Hi, thanks for the help. I tried again but I still have the same problem:
```
# cat /etc/apt/sources.list.d/jason-scheunemann-ppa-maverick.list 
deb http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu lucid main
#deb-src http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu lucid main 
```

```
# apt-get install -y sopcast-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib32stdc++5 sp-auth
The following NEW packages will be installed
  lib32stdc++5 sopcast-player sp-auth
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 182kB/709kB of archives.
After this operation, 3,232kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/ lucid/main lib32stdc++5 amd64 3.3.6~ppa~lucid2 [182kB]
Fetched 182kB in 0s (239kB/s)       
(Reading database ... 156050 files and directories currently installed.)
Unpacking lib32stdc++5 (from .../lib32stdc++5_3.3.6~ppa~lucid2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/lib32stdc++5_3.3.6~ppa~lucid2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib32/libstdc++.so.5.0.7', which is also in package ia32-libs 20090808ubuntu9
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package sp-auth.
Unpacking sp-auth (from .../sp-auth_3.2.6~ppa1~lucid7_amd64.deb) ...
Selecting previously deselected package sopcast-player.
Unpacking sopcast-player (from .../sopcast-player_0.4.0~ppa1~lucid4_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/lib32stdc++5_3.3.6~ppa~lucid2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

After this I can not use apt-get for anything without manually locating and removing the packages and the ppa.
```
root@emenius-desktop:/home/emenius# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 sp-auth : Depends: ia32-libs (< 2.7ubuntu17) but 20090808ubuntu9 is installed or
                    lib32stdc++5 but it is not installed
E: Unmet dependencies. Try using -f.
root@emenius-desktop:/home/emenius# apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed
  lib32stdc++5
The following packages have been kept back:
  nautilus
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/182kB of archives.
After this operation, 844kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 156135 files and directories currently installed.)
Unpacking lib32stdc++5 (from .../lib32stdc++5_3.3.6~ppa~lucid2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/lib32stdc++5_3.3.6~ppa~lucid2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib32/libstdc++.so.5.0.7', which is also in package ia32-libs 20090808ubuntu9
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/lib32stdc++5_3.3.6~ppa~lucid2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

Any ideas what's going wrong here? Package was working fine in lucid for me, it's odd because It seems I'm the only one with this problem!

Any help will be greatly appreciated.
Thanks, Rhys

---

### Post by realzippy on 2010-10-18
Probably you get the same error when installing the Libstcc before sopcast.,
but try [it]("http://ftp.de.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_amd64.deb").
If same error,you could temporarily uninstall the ia32libs package to avoid the conflict...
I am not on a 64 bit machine in the moment,so I do not have the problem
and cannot reproduce your issue.

---

### Post by thruxton on 2010-12-14
Hey, I have just installed sopcast-player 0.4.1~ppa1~maverick2 but the default channel guide points to: [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)
Nothing happens when you try to load channels, is there a working channel guide somewhere else?

---

### Post by realzippy on 2010-12-21
Nah,it was temporarily down.happens sometimes...

---

### Post by c-m on 2010-12-21
Sopcast links are no longer working for me in firefox. I'm getting the unknown protocall.

---

### Post by howefield on 2010-12-21
Try entering the following commands in terminal.

```
gconftool-2 -t string -s /desktop/gnome/url-handlers/sop/command "/usr/bin/sopcast-player %s"
```
```
gconftool-2 -t bool -s /desktop/gnome/url-handlers/sop/needs_terminal false
```
```
gconftool-2 -t bool -s /desktop/gnome/url-handlers/sop/enabled true
```

---

### Post by c-m on 2010-12-21
That worked a treat thanks. I'd have never have known that.

---

### Post by wyth on 2011-02-27
> **serpfra said:**
> Hi 
I have SopCast Player 0.4.0 on Ubuntu 10.04 and is working great.
But I'd like to know how can I remove some Bookmarks?
Please help.
T Y

Don't know if you ever got the answer, but for anyone else, check in ~/.pySopCast. Your bookmarks are stored in the sqlite pySopCast.db database. To edit them, you'll need an application like SQLite Database Browser (in the repositories).

---

### Post by DarkTide on 2011-04-05
yesterday I contacted sopcast.com about that very subject. They said  they would be happy to add SopCast Player to the downloads page. I  assume it will happen sometime soon. I will definitely keep everyone  updated. Now if I could just get a Linux mag to review the player...

---

### Post by Bo Rosén on 2011-04-21
I'm playing around with Natty, a clean install except for my old /home. I installed sopcast-player from the ferramroberto repository and the program runs fine when started on its own. But links won't work in Firefox, I get the 'sop protocol not associated with any program' message.

Not sure how much Natty differs from Maverick here, but the gconf settings seem fine.
Command points to /usr/bin/sopcast-player %s (I tried "%s" too)
Enabled and 'needs terminal' disabled.

In Firefox I have 'network.protocol-handler.app.sop customised* string sopcast-player'

*Or words to that effect, it's in Swedish.

Any ideas?

[COLOR=Red]Solved it[COLOR=Black]: [/COLOR][/COLOR]In Firefox, I needed to go to Edit --> Options --> Programs and add the path to sopcast-player manually for the 'sop' entry. It was set to 'always ask' but since it didn't do that... :)

---

### Post by flyguy97 on 2011-04-30
Version 0.6.0 is out on my google code page [http://sopcast-player.googlecode.com]("http://sopcast-player.googlecode.com"). Several bug fixes including fixes for fullscreen and hidden controls mode. Let me know if you are having any issues.

Please Note: I have submitted a build request for version 0.6.0 through my PPA, however the build servers are extremely backed up because of Natty. It may be until the 5th of May until the update is available through my ppa. Sorry for the inconvenience. Please give it a try and tell me what you think.

Cheers,
Jason

---

### Post by tsx2424 on 2011-06-15
It's great app and work great.I using external player as mplayer as it is very stable.but mplayer does not show the url such as "http://127.0.0.1:37099/tv.asf" 

How can I see these url in mplayer? 
Sopplayer showing url When I select channel.but disappear in few second.

---

### Post by his221 on 2011-08-14
Hi!

For those of your unable to open the sop links automatically from chrome or firefox in Ubuntu Natty, you have to change the file [FONT="Courier New"]/usr/share/applications/sopcast-player.desktop[/FONT] with the following text:
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=SopCast Player
GenericName=Internet Television
Comment=GUI front-end to SopCast
TryExec=sopcast-player
Exec=sopcast-player %U
Icon=sopcast-player
Terminal=false
Type=Application
Categories=GNOME;AudioVideo;P2P;Video;TV;GTK;
StartupNotify=true
MimeType=video/x-ms-wmv;x-scheme-handler/sop;
```

Once done, you just have to run: ```
sudo update-desktop-database
``` and without restarting Ubuntu, the sop links work.

The modifications I did where based on this article: [How to configure chrome to open magnet url's with deluge?]("http://askubuntu.com/questions/44849/how-to-configure-chrome-to-open-magnet-urls-with-deluge")
I would be nice if the changes where submitted to the code ppa directly.

---

### Post by vall on 2011-08-20
Hi,

I tried installing sopcast player 0.7.2 on Fedora 15 64bit. When I run it I get:

/usr/bin/sopcast-player: line 2: 13709 Segmentation fault      (core dumped) /usr/bin/python /usr/share/sopcast-player/lib/sopcast-player.py $@

with Python 2.7.  When I run it with python2.5 it seems to run but I miss some libraries, which I don't know how to install:

Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 22, in <module>
    import gobject
ImportError: No module named gobject

I need help to get it working with the default python2.7.

If I run the commandp-line client like that it works fine:

sp-sc sop://broker.sopcast.com:3912/106491 3908 8908 > /dev/null &
 mplayer [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf)

---

### Post by lf28 on 2011-09-24
Hi,

I have just installed the sopcast player  from the PPA in Ubuntu 11.04. The installation finishes without any  problem. But the player cannot be launched at all. When I open it from  utility, nothing happens. Then I launch it from terminal, it gives the  following error messages:

Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 790, in <module>
    pySop.main()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 152, in main
    self.populate_channel_treeview(chinese)        
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 332, in populate_channel_treeview
    channel_group_iter = self.channel_treeview_model.append(None, self.prepare_row_for_channel_treeview_model(channe  l_group))
TypeError: value is of wrong type for this column

Have tried remove and reinstall, no luck. Thanks a lot!!!

---

### Post by B70 on 2011-12-04
Hello,

I would be happy if you could help me.

I use Ubuntu 11.10 and I installed SopCast Player. After a while, the program refused to start. I use 2ClickUpdate and it seems that the application has replaced the program with Ferramosca's version. I uninstalled the program and I installed Ferramosca's program. After a while, even this program has not started. I uninstalled and reinstalled, alternatively, both programs, but none could be started. I do not know what could be done in this situation.

---

### Post by wiresquire on 2012-04-04
Any chance of adding support for Precise Pangolin to the repository? ;)

---

### Post by wiresquire on 2012-04-06
I tried manually adding the oneiric packages to Precise (after ensuring that the dependencies were installed),and I get a segmentation fault :(

Does anyone have any info on how to get sopcast going on Precise Pangolin 64 bit?

---

### Post by wiresquire on 2012-04-06
Well, to answer my own question - kind of...

a) You can install the latest windows Sopcast player under wine.

b) The problem with the ubuntu/linux sopcast player appears to be in the sopcast-player package. You can actually still use sp-sc from the sp-auth package, and manually run mplayer/VLC to view the stream. 
This seemed to be working fine for me during a short test :D
So, to summarise what I did:
*install ia32-libs, vlc, libvlc-dev
*download and install sp-auth package from repository. Note that I downloaded the oneiric ocelot AMD64 bit package for my 64 bit Precise install.
*run sp-sc, eg
sp-sc sop://broker.sopcast.com:1234/5678 3908 8908 > /dev/null
*open up vlc and select Media/Open Network Stream, and enter [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf)

Enjoy your sopcast stream

---

### Post by c-m on 2012-05-03
How do we install in Ubuntu 12.04 64bit?

Thanks

---

### Post by InSearchOf on 2012-05-07
The PPA has recently been updated for 12.04 ([https://launchpad.net/~jason-scheunemann/+archive/ppa](https://launchpad.net/~jason-scheunemann/+archive/ppa)), so it's possible to install using apt-get... but when I start the player after installation i get this error:

```

Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 32, in <module>
    from fork import ForkSOP
  File "/usr/share/sopcast-player/lib/fork.py", line 28, in <module>
    class Fork(gobject.GObject):
  File "/usr/lib/python2.7/dist-packages/gobject/__init__.py", line 60, in __init__
    cls._type_register(cls.__dict__)
  File "/usr/lib/python2.7/dist-packages/gobject/__init__.py", line 115, in _type_register
    type_register(cls, namespace.get('__gtype_name__'))
OverflowError: signed integer is greater than maximum (while registering property 'pid' for GType 'fork+Fork')

```

Any help?
System: Precise 12.04 64bit

---

### Post by freedmax on 2012-05-07
> **InSearchOf said:**
> The PPA has recently been updated for 12.04 ([https://launchpad.net/~jason-scheunemann/+archive/ppa](https://launchpad.net/~jason-scheunemann/+archive/ppa)), so it's possible to install using apt-get... but when I start the player after installation i get this error:

```

Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 32, in <module>
    from fork import ForkSOP
  File "/usr/share/sopcast-player/lib/fork.py", line 28, in <module>
    class Fork(gobject.GObject):
  File "/usr/lib/python2.7/dist-packages/gobject/__init__.py", line 60, in __init__
    cls._type_register(cls.__dict__)
  File "/usr/lib/python2.7/dist-packages/gobject/__init__.py", line 115, in _type_register
    type_register(cls, namespace.get('__gtype_name__'))
OverflowError: signed integer is greater than maximum (while registering property 'pid' for GType 'fork+Fork')

```

Any help?
System: Precise 12.04 64bit

The same output for me.

---

### Post by tobson on 2012-05-07
I had the same problem but solved by installing sopcast from *ppa:ferramroberto/sopcast*. After installastion I got an segmetation fault but inserting only a # on the first position of the line *import vlc_1_0_x* in */usr/share/sopcast-player/lib/VLCWidget.py* solved this issue and Sopcast is now working fine.

---

### Post by InSearchOf on 2012-05-07
Kind of working with tobson's workaround. Thanks :-)
Segmentation fault is still happening from time to time when opening channels. I do though suspect that it only happens when trying to open dead sop-links, but do not know how to confirm this at this point.

---

### Post by tobson on 2012-05-11
today there was an update in the ppa i'm using (*ppa:ferramroberto/sopcast*) and and it is still working! :) Don't know what was wrong with other one (*ppa:jason-scheunemann/ppa*) although there were know the same versions. But havent tried the other one again.

---

### Post by flyguy97 on 2012-05-11
> **tobson said:**
> today there was an update in the ppa i'm using (*ppa:ferramroberto/sopcast*) and and it is still working! :) Don't know what was wrong with other one (*ppa:jason-scheunemann/ppa*) although there were know the same versions. But havent tried the other one again.

I can tell you my ppa is working (ppa:Jason-Scheunemann/ppa). The fix was to finally drop support for pre 1.1.0 versions of sopcast. If you have any further issues please post a support ticket at my google code page and I will fix it as soon as possible.

Warmest regards,
Jason

---

### Post by tobson on 2012-05-12
> **flyguy97 said:**
> I can tell you my ppa is working (ppa:Jason-Scheunemann/ppa). The fix was to finally drop support for pre 1.1.0 versions of sopcast. If you have any further issues please post a support ticket at my google code page and I will fix it as soon as possible.

Warmest regards,
Jason

Sorry if this came across wrong. I can tell you that i'm using your ppa awhile now for installing sopcast (also right now) anad mostly without any problems. Thank you it. Just wanted only give an alternative if someone needs a quick sollution.

regards
tobson

---

### Post by toaksie on 2012-05-13
Is there any way to configure the buffer.  I have used sopcast in Windows and have no issue with the buffer but on Ubuntu 12.04 sopcast-player only manages to reach 30% buffer and freezes every few seconds

---

### Post by flyguy97 on 2012-05-19
> **toaksie said:**
> Is there any way to configure the buffer.  I have used sopcast in Windows and have no issue with the buffer but on Ubuntu 12.04 sopcast-player only manages to reach 30% buffer and freezes every few seconds

I'm not sure what you mean by configure the buffer. Could you please explain??

Regards,
Jason

---

### Post by sakamoto on 2012-05-20
i installed the sopcast player but the refreshing of the sopcast player channel guide constantly results in 'server down'.

any workaround or is the server really down? do i have to install python 2.5? thank you

FYI: ubuntu 10.04 with vlc 1.1.13 installed

edit: i did some additional verification, if i open the available sopcast sources in firefox i always receive an xml parsing error


[COLOR="Red"]> XML Parsing Error: reference to invalid character number
Location: [http://www.sopcast.com/chlist.xml](http://www.sopcast.com/chlist.xml)
Line Number 144, Column 11:Phone: 359/886-701-316</description></channel><channel id="130701" type="0" btype="0" language="en"><name en="Khutba Juma" cn="">MTA</name><status>2</status><region en="Canada" cn="&#21152;&#25343;&#22823;">CA</region><class en="Education" cn="&#25945;&#32946;&#31867;">8</class><user_count>1</user_count><sn>4120</sn><visit_count>12</visit_count><start_from>Sun, 20 May 2012 13:29:43 GMT</start_from><stream_type>wmv</stream_type><kbps>1563</kbps><qs>58</qs><qc>79</qc><sop_address><item>sop://218.106.52.252:3912/130701</item></sop_address><description cn="">Description:Khutba Juma
----------^[/COLOR]
 

[http://www.sopcast.com/chlist.xml](http://www.sopcast.com/chlist.xml)
[http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)
[http://www.sopcast.cn/chlist.xml](http://www.sopcast.cn/chlist.xml)
[http://www.sopcast.cn/gchlxml](http://www.sopcast.cn/gchlxml)
[http://www.sopcast.org/chlist.xml](http://www.sopcast.org/chlist.xml)
[http://www.sopcast.org/gchlxml](http://www.sopcast.org/gchlxml)

---

### Post by sakamoto on 2012-05-20
nevermind - something was apparently broken with those sources but fixed in the meantime. very nice app :D thank you

---

### Post by gordintoronto on 2012-05-20
I copied the ppa address in #474 above, got:
Failed to fetch [http://ppa.launchpad.net/Jason-Scheunemann/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/Jason-Scheunemann/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/Jason-Scheunemann/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/Jason-Scheunemann/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

However, this worked in Mint 12 with Cinnamon:
ppa:ferramroberto/sopcast

Thanks, folks!

---

### Post by N0VAK on 2012-09-01
Hello! How to install sopcast-player 0.8.5 on Debian Squeezee ?
I recieve errors:
```
W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/'lsb_release/-cs'/binary-i386/Packages.gz  404  Not Found

W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/'lsb_release/main/binary-i386/Packages.gz  404  Not Found

W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/squeezee/main/binary-i386/Packages.gz  404  Not Found
```

---

