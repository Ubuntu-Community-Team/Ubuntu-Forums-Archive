---
title: "[SOLVED] Realplayer plugin in Opera 9.25 - anybody got it working?"
date: 2008-01-12
forum: Desktop Environments
---

### Post by itsjustarumour on 2008-01-12
Hi,

A simple plea for help!

Has anybody got the RealPlayer browser plugin working properly in Opera 9.25, when viewing embedded streaming content on the BBC News web site?

If so - please could someone be kind enough to post up the contents of their plugin list (Tools --> Advanced --> Plugins) as I've got myself into a terrible mess!

Thanks in advance!

itsjustarumour

---

### Post by ubuntu-freak on 2008-01-13
I don't use Opera but my how-to might help. Gets everything streaming in Firefox properly.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Remove realplayer and install helix and helix mozilla too.

You might need to copy plugins to your Opera plugins folder or symlink them. Not sure if it likes symlinks. To symlink you
 
**sudo ln -s /fileorfoldernameandlocation /destination** 
 
If my howto helps, please reply in that thread as it keeps it alive.
 
Thanks,
 
Nathan

---

### Post by itsjustarumour on 2008-01-13
> **reassuringlyoffensive said:**
> I don't use Opera but my how-to might help. Gets everything streaming in Firefox properly.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Remove realplayer and install helix and helix mozilla too.

You might need to copy plugins to your Opera plugins folder or symlink them. Not sure if it likes symlinks. To symlink you
 
**sudo ln -s /fileorfoldernameandlocation /destination** 
 
If my howto helps, please reply in that thread as it keeps it alive.
 
Thanks,
 
Nathan


Hi Nathan,

Thanks very much for the reply, I think our paths have crossed a couple of times before on the forums with regards to Realplayer plugin issues!

I've been trying to get the RealPlayer plugin to work with Opera because, well, I've finally given up on trying to get it to work in Firefox.  

I must add at this point that RealPlayer in the only acceptable option for me for viewing embedded streams, as I need the ability to fast-forward and reverse through streams and watching half-hour interviews on the BBC news site where I need to be able to keep going back to the same point fifteen minutes into a piece is a real pain in the a*se!  And no other player provides this functionality.  I've tried the Helix player by the way, but get the same problems.  So until I can get this sorted, I've having to continue to boot into Windows just to look at the BBC news clips.  And, well, I needn't say any more about that I think!

By way of a bit of history, trying to get to the bottom of why the RealPlayer plugin won't work properly for myself and many, many, many others on both this forum and elsewhere has become a bit of a "pet project" for me over the last year.  Opera/RealPlayer used to work fine, as did Firefox 1.5/Realplayer (most of the time).  But everything broke around the time that Firefox 2.0 was released.  I have tried - and no exageration here - EVERY how-to on this forum and elsewhere.  I've tried various versions of RealPlayer from the Real site, Feisty repos, Gutsy repos, Debian repos, and a couple of customised versions that had been packaged by other users.  I've tried reinstalling Gustsy.  And I've tried every major distro out there - openSUSE, Fedora, Mandriva, Mint, PCLinuxOS, Sabayon, Linspire, DreamLinux and several others (in fact, this is the first thing I always test when checking out a new Linux distro).  I've also posted on other forums in search of answers, including the Opera forum, the Real forum and the Helix Community forum.  The amount of time spent on this so far has now passed - no joke - the fifty hour mark!

My feeling is that there are deeper issues here than those of links, locations of various files, or conflicts between various browser plugins.  For some users, anyway.

I've spent a bit of time looking in various development forums, and have discovered some other possibilities for why the RealPlayer browser plugin doesn't work for some users. Amongst them have been possible problems with:

1. particular versions of Java
2. "plugin wrappers"
3. incompatible versions of GCC (apparently Firefox and RealPlayer need to use the same major version of GCC - currently Firefox 2.0 is 4.*.* whereas RealPlayer 10.0.9 is only 3.*.*)

There seem to be a couple of outstanding bugs that are well known within the RealPlayer/Helix developer community, but which have received little publicity or attention (because perhaps they are considered too obscure).  However as I'm neither a software developer or a computer engineer like many people here, once I get to this level I'm starting to get rather out of my depth on the technical front.

Right now - and this is the best I can get things to work in both Firefox and Opera - if I click on a link to view a stream, the window flashes up with RealPlayer and then goes blank/white.  If I click on the link to "Launch in a standalone player", this works but the playback is so choppy it is quite literally like a slide-show. And no how-to has fixed this (although I appreciate they have helped some people to fix the problem)

Perhaps the new version of RealPlayer for Linux will fix these problems.  According to one of the Real devs who responded to one of my posts last week, "RealPlayer 11.0 for Linux" will be launched "in the first quarter of 2008" - so if nothing else, theres a juicy bit of news!  :-)

Best Regards,

itsjustarumour

---

### Post by ubuntu-freak on 2008-01-13
I highly recomend you remove realplayer and try my how-to for Firefox. I stream rm and ram on the BBC just fine. Trust me. Give it a try. There is even advice for if FF doesn't realise you have mozilla-mplayer.
 
If you get it working, please reply in the how-to forum. Keeps it alive and encourages others to try it. 
 
Nathan

---

### Post by itsjustarumour on 2008-01-13
> **reassuringlyoffensive said:**
> I highly recomend you remove realplayer and try my how-to for Firefox. I stream rm and ram on the BBC just fine. Trust me. Give it a try. There is even advice for if FF doesn't realise you have mozilla-mplayer.
 
If you get it working, please reply in the how-to forum. Keeps it alive and encourages others to try it. 
 
Nathan

Ah - maybe I misunderstood what you were originally proposing.  Does that mean I'll be able to fast-forward and reverse through streams?  Thats the crucial bit...

itsjustarumour

---

### Post by ubuntu-freak on 2008-01-13
I'm not on Ubuntu now but I'm sure seek works. I should have tested that to be sure. I guess I watch short rm streams :)
 
MPlayer handles rm on it's own though (win32codecs). Helix provides ram support (BBC radio).
 
Nathan

---

### Post by itsjustarumour on 2008-01-13
OK, going back to my original question, I've decided to try again from scratch.

I've uninstalled everything Firefox/Opera/RealPlayer/Plugins/Totem/VLC etc etc and all config files, and reinstalled Firefox, Opera, Mozilla plugins and RealPlayer again.

Heres the my Opera plugins settings - is there anything obviously wrong with this?

I've read in other posts that its better to have all the plugins in the Firefox plugins directory and point everything (both Firefox and Opera) there, rather than Mozilla - is this true?

Btw - RealPlayer is installed in /usr/lib/realplay-10.0.9

---

### Post by ubuntu-freak on 2008-01-13
Looks good to me. I'm surprised you won't try my how-to for FF though. Opera is powerful but notoriously difficult regarding streaming. 
 
You won't lose anything by trying. 
 
Nathan

---

### Post by itsjustarumour on 2008-01-13
And heres my Opera Plugins list:

Plug-ins

Shockwave Flash

application/futuresplash						    spl
application/x-shockwave-flash					     swf
/usr/lib/firefox/plugins/flashplugin-alternative.so

Adobe Reader 8.0

application/pdf							                 pdf
application/vnd.adobe.xdp+xml					     xdp
application/vnd.adobe.xfd+xml					     xfd
application/vnd.fdf							      fdf
application/vnd.adobe.xfdf						xfdf
/usr/lib/firefox/plugins/nppdf.so

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

audio/x-pn-realaudio-plugin						rpm
/usr/lib/firefox/plugins/nphelix.so

MozPlugger 1.8.0 handles QuickTime and Windows Media Player Plugin

audio/wav								       wav
audio/x-wav								     wav
video/x-msvideo							           avi
video/mp4								       mp4
audio/mpeg								      mp3,mp2,mpga
audio/basic								       au
video/quicktime							             qt,mov
application/pdf							              pdf
application/postscript							  ps,eps,ai
image/tiff								          tif,tiff
video/x-ms-asf							            asf,asx
application/msword							 doc,dot,wiz,wzs
application/rtf	rtf
application/vnd.ms-excel		        xls,xl,xla,xlb,xlc,xld,xlk,xll,xlm,xlt,xlv,xlw
application/vnd.ms-powerpoint				         pot,ppa,pps,ppt,pwz
application/x-mplayer2							-
audio/x-ms-wax							         wax
video/x-ms-wmv							        wmv
application/smil							      smi,smil
audio/x-pn-realaudio-plugin				             rpm
]);video/mpeg								     mpeg,mpg,mpe
video/x-mpeg								    mpeg,mpg,mpe
video/x-mpeg2							          mpv2,mp2ve
video/msvideo								   avi
video/fli								         fli,flc
video/x-fli								        fli,flc
application/x-quicktimeplayer					    mov
image/x-macpaint							 pntg,mov
video/x-quicktime						 	  mov,qt
video/x-theora								   ogg
video/theora								    ogg
video/ogg								      ogg
video/x-ogg								    ogm,ogv
audio/mp3								     mp3
audio/x-mp3								   mp3
audio/mpeg2								  mp2
audio/x-mpeg2							         mp2
audio/mpeg3								  mp3
audio/x-mpeg3							         mp3
audio/x-mpeg								   mpa,abs,mpega
audio/x-ogg								    ogg
application/x-ogg							  ogg
application/ogg							            ogg
audio/x-flac								      flac
application/x-flac							    flac
audio/x-basic								     au,snd
audio/x-pn-wav							           wav
audio/x-pn-windows-acm						    wav
audio/x-realaudio							     ra,rm,ram
application/vnd.rn-realmedia					       rm
audio/vnd.rn-realaudio						          ra,ram
audio/vnd.rn-realvideo						          rv
image/sun-raster							     rs
image/x-sun-raster							    rs
image/x-rgb								         rgb
image/x-portable-pixmap						         ppm
image/x-portable-graymap						pgm
image/x-portable-bitmap						           pbm
image/x-portable-anymap						         pnm
image/x-tiff								             tiff,tif
image/x-xcf								           xcf
image/xcf								             xcf
application/x-gimp							         xcf
application/gimp							           xcf
application/photoshop							      psd
application/x-photoshop						             psd
application/x-pdf							          pdf
text/pdf								                pdf
text/x-pdf								               pdf
application/x-dvi							            dvi
application/x-postscript					                ps
application/x-rtf							             rtf
text/rtf									           rtf
application/x-msword					                      doc,dot
application/vnd.sun.xml.writer					           sxw
application/so7_vnd.sun.xml.writer			               sxw
application/vnd.sun.xml.writer.template				      stw
application/vnd.sun.xml.writer.global				        sxg
application/vnd.stardivision.writer					   sdw
application/vnd.stardivision.writer-global			       sgl
application/x-starwriter						        sdw
application/vnd.sun.xml.calc						     sxc
application/so7_vnd.sun.xml.calc					 sxc
application/vnd.sun.xml.calc.template				        stc
application/vnd.stardivision.calc					     sdc
application/x-starcalc							           sdc
application/vnd.lotus-1-2-3						        123, wk1
application/vnd.sun.xml.draw						     sxd
application/so7_vnd.sun.xml.draw					 sxc
application/vnd.sun.xml.draw.template				        std
application/vnd.stardivision.draw					     sda
application/x-stardraw						                   sda
application/vnd.sun.xml.impress					              sxi
application/so7_vnd.sun.xml.impress					  sxi
application/vnd.sun.xml.impress.template				sti
application/vnd.stardivision.impress					    sdd
application/vnd.stardivision.impress-packed			      sdp
application/x-starimpress						          sdd
application/mspowerpoint						        ppt,ppz,pps,pot
application/vnd.sun.xml.math						       sxm
application/so7_vnd.sun.xml.math					   sxm
application/vnd.stardivision.math					      smf
application/x-starmath						                    smf
application/vnd.oasis.opendocument.text				       odt,ODT
application/vnd.oasis.opendocument.spreadsheet			ods,ODS
application/vnd.oasis.opendocument.presentation			 odp,ODP
audio/x-pn-realaudio							            ram,ra
/usr/lib/firefox/plugins/mozplugger.so

NS4PluginProxy

application/x-opera-nsplugin						         -
/usr/lib/opera/plugins/libnpp.so

Shockwave Flash

application/futuresplash						           spl
application/x-shockwave-flash					            swf
/usr/lib/flashplugin-nonfree/libflashplayer.so

---

### Post by itsjustarumour on 2008-01-13
> **reassuringlyoffensive said:**
> Looks good to me. I'm surprised you won't try my how-to for FF though. Opera is powerful but notoriously difficult regarding streaming. 
 
You won't lose anything by trying. 
 
Nathan

Um - but can I fast forward/reverse in streams?  :-D

Btw - have to disagree with you on the Opera/Firefox front, as before I started having all these troubles Opera/Realplayer plugin always used to work out of the box on Ubuntu and openSUSE, whereas Firefox/RealPlayer needed (a minimal amount of) tweaking!

Thanks again for your posts anyway.

---

### Post by itsjustarumour on 2008-01-13
Well, I have at least made SOME progress :-) 

I've solved the issue of the choppy playback in Realplayer:

> sudo aptitude install alsa-oss

> sudo gedit /usr/lib/realplay-10.0.9/realplay

Edited this line right down at the bottom:

$REALPLAYBIN "$@"

to read:

aoss $REALPLAYBIN "$@"

Playback is now smooth when using "Launch in a standalone player".  This fix has also solved the problems of unresponsive controls and the whole applicaton locking up.

(Tested in both Firefox and Opera)  :guitar:

---

### Post by ubuntu-freak on 2008-01-13
That's great. I'm still recomending Helix as it has superceded Realplayer as far as I can tell. It's not in the repo anymore. Win32codecs play rm so I'm not sure why you need RP for your videos.
 
Nathan

---

### Post by itsjustarumour on 2008-01-13
> **reassuringlyoffensive said:**
> That's great. I'm still recomending Helix as it has superceded Realplayer as far as I can tell. It's not in the repo anymore. Win32codecs play rm so I'm not sure why you need RP for your videos.
 
Nathan

Hi Nathan,

Thanks for keeping tabs on this thread.  I'm still working on this RealPlayer thing like the stubborn old goat that I am :-)

Something you mentioned earlier on in the thread - about symbolic links - got me thinking, as they were something I didn't really know anything about.  But I've done a bit of rooting around and found this thread where a couple of users had an identical problem and setup to me:

[http://ubuntuforums.org/showthread.php?t=489653&highlight=realplayer+standalone](http://ubuntuforums.org/showthread.php?t=489653&highlight=realplayer+standalone)

I found that the RealPlayer symbolic link was broken... I've learnt how to fix that now, but unfortunately it still hasn't cured my problem! BAH - for a moment I really thought I'd found the answer I'd been seeking for so long.

Think I WILL go and give Helix another try, although last time I got exactly the same problems as with RealPlayer...

itsjustarumour

---

### Post by itsjustarumour on 2008-01-13
OK, I've uninstalled RealPlayer and installed Helix.

However, when I try and view embedded streams on the BBC News website, the Helix player opens but I get:

> Connection to server has been lost. You may be experiencing network problems. (rtsp://rm-acl.bbc.co.uk/news/media_acl/mps/fix/news/world/video/144000/bb/144568_16x9_bb.rm?title="BBC"&author="BBC"&copyright="(C)%20British%20Broadcasting%20Corporation")

And if I try and "Launch in a standalone player",  the Helix player opens but I get:

> Invalid Metafile ([http://news.bbc.co.uk/media/avdb/news/world/video/144000/bb/144568_16x9_bb.ram?ad=1&amp;ct=50](http://news.bbc.co.uk/media/avdb/news/world/video/144000/bb/144568_16x9_bb.ram?ad=1&amp;ct=50))

Any ideas?

itsjustarumour


EDIT - on some links I try I also get a message flashing up very briefly that says:

> "You are using a browser that does not support scriptable plugins..."

---

### Post by ubuntu-freak on 2008-01-13
Can you follow my how-to exactly? Helix works properly when win32codecs are installed and when you replace the standard mplayer settings with mine. Use firefox too.

Read the bottom of this thread for pure evidence. :) 
     
 [http://ubuntuforums.org/showthread.php?t=666421](http://ubuntuforums.org/showthread.php?t=666421)

Nathan

---

### Post by itsjustarumour on 2008-01-13
> **reassuringlyoffensive said:**
> Can you follow my how-to exactly? Helix works properly when win32codecs are installed and when you replace the standard mplayer settings with mine. Use firefox too.

Read the bottom of this thread for pure evidence. :) 
     
 [http://ubuntuforums.org/showthread.php?t=666421](http://ubuntuforums.org/showthread.php?t=666421)

Nathan

Yup, followed the how-to exactly.  Been through it twice now - Firefox only - same result...


EDIT - just tried again, no joy.  Each time I've "cleaned up" beforehand all old Helix files etc. 

Can't even listen to radio on the BBC with Helix - no sound...

---

### Post by ubuntu-freak on 2008-01-13
Did you delete the firefox folder in your home directory and the rest of my advice for that issue you have? Posted it further down.
 
Nathan

---

### Post by itsjustarumour on 2008-01-14
> **reassuringlyoffensive said:**
> Did you delete the firefox folder in your home directory and the rest of my advice for that issue you have?

No, as for some reason I dont have a Firefox folder at /home/(username)/.firefox

Theres a /home/(usename)/.mozilla folder though - would that be it?

itsjustarumour

---

### Post by itsjustarumour on 2008-01-14
OK, I backed up my bookmarks etc and then deleted /home/(username)/.mozilla

Followed your how-to all the way through, reinstalled helix, mozilla plugins etc etc - still same thing - Helix won't open.

Clicking on a link on the BBC News website gives:

> Connection to server has been lost. You may be experiencing network problems. (rtsp://rm-acl.bbc.co.uk/news/media_acl/mps/fix/news/world/video/144000/bb/144648_16x9_bb.rm?title="BBC"&author="BBC"&copyright="(C)%20British%20Broadcasting%20Corporation")

"Open in standalone player" gives:

> Connection to server has been lost. You may be experiencing network problems. (rtsp://rm-acl.bbc.co.uk/news/media_acl/mps/fix/news/uk/video/144000/bb/144652_16x9_bb.rm?title="BBC"&author="BBC"&copyright="(C)%20British%20Broadcasting%20Corporation")

---

### Post by ubuntu-freak on 2008-01-14
This is madness! lol. I have people saying thanks and that it works great, and a few are struggling just as you are.
 
Have you tried other sites with rm and ram streams?
 
Are the xine plugins removed? Forgot to add that to my how-to.
 
Nathan

---

### Post by itsjustarumour on 2008-01-15
> **reassuringlyoffensive said:**
> This is madness! lol. I have people saying thanks and that it works great, and a few are struggling just as you are.
 
Have you tried other sites with rm and ram streams?
 
Are the xine plugins removed? Forgot to add that to my how-to.
 
Nathan

Hi again Nathan,

Yes, the xine plugins are removed.  Seem to have taken the rest of Totem with them too, which is a problem in itself as Totem/GStreamer didn't work very well and I had to change to the Xine back end to watch DVD movies... BAH!

itsjustarumour

---

### Post by ubuntu-freak on 2008-01-15
> **itsjustarumour said:**
> Hi again Nathan,

Yes, the xine plugins are removed.  Seem to have taken the rest of Totem with them too, which is a problem in itself as Totem/GStreamer didn't work very well and I had to change to the Xine back end to watch DVD movies... BAH!

itsjustarumour

 
Someone told me they had to delete the Firefox plugin dat file lots of times and then everything worked. It's a bug with FF.
 
I've added a section to my 2nd post regarding DVD playback. Give it try! Improves encrypted DVD support (or completely solves it). 
 
Nathan

---

### Post by itsjustarumour on 2008-01-15
> **reassuringlyoffensive said:**
> Someone told me they had to delete the Firefox plugin dat file lots of times and then everything worked. It's a bug with FF.
 
I've added a section to my 2nd post regarding DVD playback. Give it try! Improves encrypted DVD support (or completely solves it). 
 
Nathan

Yup, I tried deleting the Firefox plugin dat file - read about that on another thread somewhere.

OK - will go have another look at your thread.

Cheers,

itsjustarumour

---

### Post by ubuntu-freak on 2008-01-17
> **itsjustarumour said:**
> Yup, I tried deleting the Firefox plugin dat file - read about that on another thread somewhere.

OK - will go have another look at your thread.

Cheers,

itsjustarumour

 
I've changed my how-to. 
 
Start it all over again and replace the mplayer conf again as it has be changed. It no longer manages rm, helix and smil. 

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) 

Nathan

---

### Post by robc02 on 2008-02-14
I can't get streaming to work in Opera either. I have followed Nathan's guide and got it working OK in Firefox, but no joy with Opera.

In order to Flashplayer working I have had to install an older version of Flash in /usr/lib/opera/plugins. To prevent a clash with the newer version in /usr/lib/mozilla/plugins I have disabled that path in Opera and copied the mplayer plugins to /usr/lib/opera/plugins. I have also enabled /usr/lib/realplay-10.0.9/plugins and this may be where my problems lie.

When I examine the list of plugins recognised by Opera (tools, preferences, advanced, content, plugin options) nothing shows in the realplayer folder. When looking in the realplay-10.0.9/plugins folder I see loads of plugins for playing various file formats. There are also lots of plugins in other realplay-10.0.9 subfolders. Why don't these show up in Opera? Should there be one, higher level, Realplayer plugin that is recognised? If so where is it? I have tried searching my filesystem but can't see anything that looks promising.

Hope someone can help.

---

### Post by itsjustarumour on 2008-02-14
> **robc02 said:**
> I can't get streaming to work in Opera either. I have followed Nathan's guide and got it working OK in Firefox, but no joy with Opera.

In order to Flashplayer working I have had to install an older version of Flash in /usr/lib/opera/plugins. To prevent a clash with the newer version in /usr/lib/mozilla/plugins I have disabled that path in Opera and copied the mplayer plugins to /usr/lib/opera/plugins. I have also enabled /usr/lib/realplay-10.0.9/plugins and this may be where my problems lie.

When I examine the list of plugins recognised by Opera (tools, preferences, advanced, content, plugin options) nothing shows in the realplayer folder. When looking in the realplay-10.0.9/plugins folder I see loads of plugins for playing various file formats. There are also lots of plugins in other realplay-10.0.9 subfolders. Why don't these show up in Opera? Should there be one, higher level, Realplayer plugin that is recognised? If so where is it? I have tried searching my filesystem but can't see anything that looks promising.

Hope someone can help.


Hi Robc,

I never got this working, and frankly when I realised I'd spent over FOUR DAYS OF MY LIFE trying to fix this, I just decided enough was enough.  I'm just waiting for Realplayer 11 for Linux (if it ever appears) to see if that cures the problem, and in the meantime using the "Launch in standalone player" button which isn't perfect but at least I've got that much to work now.

The BBC site is the one I look at the most.  The weird thing is, OCCASIONALLY a link on that site works eg:

This one works:

[http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_4860000/newsid_4860200?redirect=4860274.stm&news=1&nbram=1&bbram=1&nbwm=1&bbwm=1](http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_4860000/newsid_4860200?redirect=4860274.stm&news=1&nbram=1&bbram=1&nbwm=1&bbwm=1)

whereas this one does not:

[http://news.bbc.co.uk/player/nol/newsid_4090000/newsid_4097900/4097948.stm?bw=bb&mp=rm&news=1&bbcws=1](http://news.bbc.co.uk/player/nol/newsid_4090000/newsid_4097900/4097948.stm?bw=bb&mp=rm&news=1&bbcws=1)

Whats the difference?  Well, examining the links, there is one (the one that works includes some sort of "redirection")... but I have no idea what it means.

Be curious to know if you get the same result!

---

### Post by itsjustarumour on 2008-02-14
Just as a follow-up, heres what I get if I run Opera in terminal, go to the BBC website and then try and play one of streaming links with the Realplayer plugin:

> ian@COOLERMASTER:~$ opera
GCJ PLUGIN: thread 0x806f1e0: NP_GetValue
GCJ PLUGIN: thread 0x806f1e0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x806f1e0: NP_GetValue return
GCJ PLUGIN: thread 0x806f1e0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x806f1e0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x806f1e0: NP_GetValue
GCJ PLUGIN: thread 0x806f1e0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x806f1e0: NP_GetValue return
GCJ PLUGIN: thread 0x806f1e0: NP_GetValue
GCJ PLUGIN: thread 0x806f1e0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x806f1e0: NP_GetValue return
Calling realplay
playeripc: Got command Version 1
playeripc: Got command Embed name='mediaPlayerControl' id='objrpcontrols' controls='ControlPanel' console='av' type='audio/x-pn-realaudio-plugin' showcontrols='1' showstatusbar='1' 

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute id

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute showcontrols

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute showstatusbar
playeripc: Got command Browser 0 'Mozilla/4.78 (X11; Linux i686; U; en) Opera 9.50' 0 0
playeripc: Got command UnsetWindow 0
All consoles have been closed
playeripc: Got command Embed name='mediaPlayerObject' id='embedbbRPImageWindow' src='/media/avdb/news/science_nature/video/152000/bb/152266_16x9_bb.ram?ad=1&ct=50' controls='ImageWindow' console='av' type='audio/x-pn-realaudio-plugin' autostart='true' showcontrols='0' showstatusbar='1' scriptcallbacks='onPlayStateChange,onClipOpened,onClipClosed' 

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute id

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute showcontrols

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute showstatusbar
playeripc: Got command Embed name='mediaPlayerStatus' id='objrpstatus' controls='StatusBar' console='av' type='audio/x-pn-realaudio-plugin' showcontrols='1' showstatusbar='1' 

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute id

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute showcontrols

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute showstatusbar
playeripc: Got command Embed name='mediaPlayerControl' id='objrpcontrols' controls='ControlPanel' console='av' type='audio/x-pn-realaudio-plugin' showcontrols='1' showstatusbar='1' 

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute id

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute showcontrols

** (realplay.bin:10412): WARNING **: Ignoring unknown attribute showstatusbar
playeripc: Got command Browser 1 'Mozilla/4.78 (X11; Linux i686; U; en) Opera 9.50' 0 0
playeripc: Got command SetXID 1 85983235 0 0 400 224 0 0 0 0 1

** (realplay.bin:10412): WARNING **: Width and height for window 1 are invalid

(realplay.bin:10412): Gtk-WARNING **: Attempting to add a widget with type HXPlayer to a container of type HXBin, but the widget is already inside a container of type HXBin, the GTK+ FAQ at [http://www.gtk.org/faq/](http://www.gtk.org/faq/) explains how to reparent a widget.
playeripc: Got command Browser 2 'Mozilla/4.78 (X11; Linux i686; U; en) Opera 9.50' 0 0
playeripc: Got command SetXID 2 85983237 0 0 400 30 0 0 0 0 1

** (realplay.bin:10412): WARNING **: Width and height for window 2 are invalid
playeripc: Got command Browser 3 'Mozilla/4.78 (X11; Linux i686; U; en) Opera 9.50' 0 0
playeripc: Got command SetXID 3 85983239 0 0 400 30 0 0 0 0 1

** (realplay.bin:10412): WARNING **: Width and height for window 3 are invalid
playeripc: Got command SetXID 1 85983235 0 0 400 224 0 0 0 0 1

** (realplay.bin:10412): WARNING **: Width and height for window 1 are invalid
playeripc: Got command SetXID 2 85983237 0 0 400 30 0 0 0 0 1

** (realplay.bin:10412): WARNING **: Width and height for window 2 are invalid
playeripc: Got command SetXID 3 85983239 0 0 400 30 0 0 0 0 1

** (realplay.bin:10412): WARNING **: Width and height for window 3 are invalid
playeripc: Got command SetXID 1 85983235 0 0 400 224 0 0 0 0 1

** (realplay.bin:10412): WARNING **: Width and height for window 1 are invalid
playeripc: Got command SetXID 2 85983237 0 0 400 30 0 0 0 0 1

** (realplay.bin:10412): WARNING **: Width and height for window 2 are invalid
playeripc: Got command SetXID 3 85983239 0 0 400 30 0 0 0 0 1

** (realplay.bin:10412): WARNING **: Width and height for window 3 are invalid
playeripc: Got command NewStream 1 0 [http://news.bbc.co.uk/media/avdb/news/science_nature/video/152000/bb/152266_16x9_bb.ram?ad=1&ct=50](http://news.bbc.co.uk/media/avdb/news/science_nature/video/152000/bb/152266_16x9_bb.ram?ad=1&ct=50) audio/x-pn-realaudio 0
/usr/bin/realplay: line 75: 10412 Segmentation fault      (core dumped) aoss $REALPLAYBIN "$@"


For what its worth, I've been to [http://www.gtk.org/faq/](http://www.gtk.org/faq/)
 to find out how to "re-parent the widget" but this assumes rather more technical savvy than I possess, alas.

---

### Post by itsjustarumour on 2008-02-14
This post was a duplicate which I've deleted - please ignore!

---

### Post by robc02 on 2008-02-14
Neither of those links worked for me in Opera; both worked in Firefox but only in "Standalone Realplayer". 
At least part of my problem is, I think, that Opera cannot see my Realpayer plugins.

---

### Post by itsjustarumour on 2008-02-14
> **robc02 said:**
> Neither of those links worked for me in Opera; both worked in Firefox but only in "Standalone Realplayer". 
At least part of my problem is, I think, that Opera cannot see my Realpayer plugins.

Oh well, wish I could help but I'm stumped!

---

### Post by robc02 on 2008-02-14
I just found this on the mlalyer plugin ( [http://mplayerplug-in.sourceforge.net/faq.php]("http://mplayerplug-in.sourceforge.net/faq.php")) website under FAQ:

**[I]How do I make mplayerplug-in work in Opera?(Not recommended)**
Make sure that you have gecko-sdk 1.6 newer versions will not work properly with Opera
Download the source code then do these following commands in the source code directory:

./configure --enable-x  [--with-gecko-sdk={path} ]
make
cp mplayerplug-in.so /usr/lib/opera/plugins
ln -s /usr/lib/mozilla/libxpcom.so /usr/lib [/I]

I am using the mplayer plugin in Firefox, as per Nathan's guide, but I also installed Real player as per the same guide. I am not sure how the two fit together. However, following the guide solved all of my audio streaming problems in Firefox.

---

### Post by ubuntu-freak on 2008-02-14
Glad you got it working.
 
The reason they work together so well is because MPlayer is very configurable. My settings in the how-to disable Real Media playback with the MPlayer plugin so that RealPlayer's plugin can handle it instead. 64-bit users should let MPlayer handle them however, as RealPlayer is a 32-bit application only.
 
Nathan

---

### Post by itsjustarumour on 2008-02-27
For those who weren't aware, the BBC launched the new version of their News site on Monday of this week.  

The good news for Linux users is... streaming news video clips now work much better with the RealPlayer plugin!!!!! :guitar:

I've tested this with both Firefox and Opera, and although not ALL of the news video clips work, I tested 20 at random and 13 worked.  Previously, these had almost NEVER worked.

Good to see that Aunty Beeb has finally made some changes to their site to cure at least some of the problems experienced by Linux/Realplayer users.  Many people had experienced problems since the BBC modified their site back in January 2007, including some rather heavy site-specific customisations which basically broke this functionality for many Linux users.

:-D

---

