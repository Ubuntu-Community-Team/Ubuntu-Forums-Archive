---
title: "Sopcast (streaming tv) on ubuntu"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Naegling23 on 2006-10-07
Im running kubuntu, and would really like to get sopcast ( [www.sopcast.org](www.sopcast.org) )running so that I can watch my flyers games this year.  Apparently it runs under linux, but I was unable to get it working (I could install it, just not get it working).  Has anyone gotten this program to work?  I would appriciate some help.  I couldnt seem to find any good/current guides.

---

### Post by neodarksaver on 2007-05-15
[http://ubuntuforums.org/showthread.php?t=258049](http://ubuntuforums.org/showthread.php?t=258049)

if u still need help after all this time.

---

### Post by LPGDEV on 2007-08-06
I have installed sopcast and it works well. I would like to associate firefox sop links to sopcast. I have added the following lines of code to the about:config in firefox:

network.protocol-handler.warn-external.sop   user set  boolean  false
network.protocol-handler.external.sop            user set  boolean  true
network.protocol-handler.app.sop                   user set  string      /usr/bin/gsopcast

This works by opening the sopcast player. However it does not open the link i clicked directly. What do I need to add for this to happen?

Thanks

---

### Post by Steve_H on 2007-08-11
Did you manage to get this fixed? I've the same problem....Cheers

---

### Post by teetee on 2007-09-08
I am also interested... so, anyone?

---

### Post by Il Capitano on 2007-09-19
Same here. Any ideas?

---

### Post by Trab on 2007-09-19
while i have no experience in this field, i would reccomend you would need to somehow PASS the link itself to sopcast in firefox? for example (this will NOT Work, its just a sample)
```

network.protocol-handler.app.sop user set string /usr/bin/gsopcast $l

```

you will have to look up how sopcast handles outside links passed to it (via command line methods) and how firefox handles urls as a variable.


cheers,
Trab

---

### Post by Il Capitano on 2007-09-29
All right. I found out how to watch sopcast streaming from the command line by means of a "sop://sop.sopcast.org:1234/5678"-type of link:

./sp-sc [-b ipaddr] [-u username:password] [-n out:total] <sop://url> <localport> <playerport>

eg. : sp-sc sop://sop.sopcast.org:1234/5678 3908 8908.

After entering this in the command line, you can watch the streaming by opening the url [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf) in a media player.

This leaves me however with two remaining problems:
- I haven't found out yet how firefox handles url's as variables
- I not only want to start the streaming, but i also want totem to open the url [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf) when i click on the sop:// link.

---

### Post by Il Capitano on 2007-09-29
I got it working (although rather dirty) doing the following:

1. Make script sopcast.sh with the following code:

```
#!/bin/bash
# Script to start totem mediaplayer using sopcast streams from firefox

sp-sc $1 3908 8908 &
sleep 30
totem http://localhost:8908/tv.asf &
```

This script calls the sopcast command line with the link passed from firefox and the fixed ports as arguments. It will sleep for 30 seconds to let sopcast load the channel. It then will start totem with the url on which sopcast streams.

I saved the script in my homedir/.scripts/

2. Edit about:config in firefox

Add the following lines (replacing yourdirectoryforsopcast with the directory in which you have saved the script):
```

network.protocol-handler.warn-external.sop user set boolean false
network.protocol-handler.external.sop user set boolean true
network.protocol-handler.app.sop user set string yourdirectoryforsopcast/sopcast.sh
```

I am new to linux, so my script isn't the best. For example, it is not enough to close totem to stop the streaming. You need to kill the processes sopcast.sh and sp-sc manually. Any suggestions for improvement are welcome.

---

### Post by themstpt on 2007-10-03
hi,
this is my first time posting here.
I have put this:

xterm -hold -e sp-sc $1 3908 8908 &

instead, because if some error happens in sp-sc now you know.
The only disadvantage now is that it opens a xterm window :P

The only bug :( is that if there is a error...totem still opens.

---

### Post by Naegling23 on 2007-10-08
hmmm, seems that I have sopcast working, and can watch whatever is listed.  However, if I paste a link into the window and click launch, the program segfaults.

Ive tried the 2.8 as well as the 3.1 versions, neither work.  Ive also tried the qsopcast player, but I cant find the window to put in a custom channel....very annoying

---

### Post by begemot1 on 2007-10-08
I have the same situation:  I can click on any of the listed channels on the gsopcast GUI, and most of them do work - launch mplayer - but I can't figure out how to enter the information for a channel that I find listed elsewhere (e.g. on myp2p.eu).  Gsopcast doesn't seem to let you paste the information in any where.

Any suggestions?

---

### Post by Naegling23 on 2007-10-10
I downloaded the qsopcast client.  Everything is working just fine for me now.

The qsopcast channel box is on the top, just paste it in, and click launch at the bottom.  qsopcast seems to be a lot more polished, but then again, im a kde user, so it feels more integrated to me.

---

### Post by gadfly22 on 2007-12-07
I've tried pasting in the channel and lots of combinations of URLs and other info into the channel box at the top.  But hitting "Launch" at the bottom does nothing.  Any further suggestions?

So sopcast channels that aren't listed remain a problem.  The Windows version also comes tantalizingly close to working under Wine, but not quite.

---

### Post by JaketheSnake86 on 2007-12-25
> **gadfly22 said:**
> I've tried pasting in the channel and lots of combinations of URLs and other info into the channel box at the top.  But hitting "Launch" at the bottom does nothing.  Any further suggestions?

So sopcast channels that aren't listed remain a problem.  The Windows version also comes tantalizingly close to working under Wine, but not quite.

I got mad because of the launch button with custom channels not working, so i programmed my own software to do that.

[www.launchpad.net/soplaunch](www.launchpad.net/soplaunch)

Requires sp-sc-auth command and obviously VLC, MPlayer or some video software.

---

### Post by Jota37 on 2007-12-29
> **JaketheSnake86 said:**
> I got mad because of the launch button with custom channels not working, so i programmed my own software to do that.

[www.launchpad.net/soplaunch](www.launchpad.net/soplaunch)

Requires sp-sc-auth command and obviously VLC, MPlayer or some video software.

Thanks a lot for the program, it works quite nicely for me. 

Well, actually MPlayer crashes ("interrupted by signal 13 in module: open_stream") when trying to launch. But I then tried the "Custom" field: I entered "kaffeine" there, which I was using before anyway, and it worked. Much neater than my shell script for sure.

I have a question though: when I close Soplaunch, the sp-sc-auth program continues to run, and has to be killed manually (my script had the same "bug"). Is that how it is supposed to be right now with Soplaunch? Or was it supposed to kill sp-sc-auth on exit, but for some reason it's not doing it here for me?

Again, thanks, great job with the program.
=D>

---

### Post by csulok on 2008-01-18
this doesn't work here. when i add the url and press launch, it freezes as it should and when vlc pops up it says Unable to open 'http://localhost:8908/tv.asf'. mplayer doesn't work either.

afaik everything is installed and working (gsopcast and qsopcast works off default channel listed items).

how could i fix it?

---

### Post by Il Capitano on 2008-01-20
I get the same errors when the channel i'm trying to watch is offline. Might be the cause for your errors as well, instead of the program itself...

---

### Post by csulok on 2008-01-20
> **Il Capitano said:**
> I get the same errors when the channel i'm trying to watch is offline. Might be the cause for your errors as well, instead of the program itself...

thanks for the tip, i tried a bunch of other streams and most of them worked \o/

---

### Post by yeev on 2008-01-22
i need hepl:(
[http://ubuntuforums.org/showthread.php?t=608175&highlight=sopcast](http://ubuntuforums.org/showthread.php?t=608175&highlight=sopcast)

---

### Post by sonofabics on 2008-01-22
Have simmilar problems.
Thanks for suggestions, will try them and post if succeeded.:popcorn:

---

### Post by Benjirii on 2008-02-12
It seems I wasn't the only person that was looking for a script to start SP-SC and your videoplayer by clicking on an URL.

I've made the following script in Perl that allows people to make some easy changes in the configuration of the script (see #settings). I'm no linux expert or great at perl, but the script works perfectly for me. It also closes the sp-sc when I close my videoplayer.

Well, here's how to get it working:

1. Make a script "sopcast.pl" with the following code:
```

#!/usr/bin/perl
#SopCast program by Tuma/Benjirii

#Settings
$spsc_location 		= 	"/usr/local/bin/sp-auth/sp-sc-auth"		; # startup location for sp-sc
$vidplayer_location 	= 	"/usr/bin/vlc"					; # startup location for videoplayer
$local_port		=	"3908"						; # local port used by sp-sc
$player_port		=	"8908"						; # port on which the videoplayer listens
$startup_delay		=	"10.00"						; # startup delay between spsc and videoplayer in seconds
$killcommand		=	"killall sp-sc-auth"				; # kill command to stop sp-sc after closing videoplayer

#Variables (do not change)
$urltv 			=	"http://localhost:".$player_port."/tv.asf"	;
$endstring 		= 	"> /dev/null &"					; 
$start_spsc		= 	$spsc_location . " " . $ARGV[0] . " " . $local_port . " " . $player_port . " " . $endstring;

#Start sp-sc
system $start_spsc;

#Startup delay videoplayer
select(undef, undef, undef, $startup_delay);

#Open video
system ($vidplayer_location, $urltv);

#Kill sp-sc on closing videoplayer
system $killcommand;

```

2. Make the script executable
```

Open a terminal and use the command "chmod u+x sopcast.pl" in the directory where you saved the script.

```

3. Change the about:config in Firefox

Add the following lines to the about:config page in firefox and change the "yourdirectoryforsopcast" to where you stored the script.
```

network.protocol-handler.warn-external.sop user set boolean false
network.protocol-handler.external.sop user set boolean true
network.protocol-handler.app.sop user set string yourdirectoryforsopcast/sopcast.pl

```

Big thanks to Il Capitano for me ripping the exact descriptions of some of his instructions.

Some final words:
1) Check the settings part if all paths match and change the videoplayer if you're using something else.
2) Check if the perl directory on the first line of the script is correct, or it won't work.

If you have any questions lemme know. Hope it's of any use to someone.

Enjoy!

---

### Post by MaindotC on 2008-02-12
I just installed Gutsy and forgot to get Sopcast working before gametime.  I'm in a crisis - Sens/Sabres and I want to follow this guide [http://lj4newbies.blogspot.com/2007/12/sopcast-on-gutsy.html](http://lj4newbies.blogspot.com/2007/12/sopcast-on-gutsy.html) but I can't because the sopcast links for the .rpm's are outdated.  Can anyone send them to me or post them please?  I've googled - haven't found any that are working yet!

---

### Post by Benjirii on 2008-02-17
> **strAlan said:**
> I just installed Gutsy and forgot to get Sopcast working before gametime.  I'm in a crisis - Sens/Sabres and I want to follow this guide [http://lj4newbies.blogspot.com/2007/12/sopcast-on-gutsy.html](http://lj4newbies.blogspot.com/2007/12/sopcast-on-gutsy.html) but I can't because the sopcast links for the .rpm's are outdated.  Can anyone send them to me or post them please?  I've googled - haven't found any that are working yet!

I kinda forgot where I got mine from; and don't really use g/qsopcast anymore; but I found these googling around a bit on this site: [http://changturtle.blogspot.com/2007/10/install-qsopcast-linux-sopcast-to.html]("http://changturtle.blogspot.com/2007/10/install-qsopcast-linux-sopcast-to.html")

Scroll down to method #4 for the .deb --- **These instructions are for feisty fawn, and I haven't tried em out, so use at your own risk** ---

Or check out the lianwei's site:
[http://lianwei3.googlepages.com/home2]("http://lianwei3.googlepages.com/home2")
I see there's a 0.4.0 version of gsopcast now.

Hope this helps!

---

### Post by ryukent on 2008-02-21
For an easier way to install SopCast, the GUI and setup firefox to pass URLs, please see this guide:

[http://www.linux.ryukent.co.uk/show.php?id=36]("http://www.linux.ryukent.co.uk/show.php?id=36")

It includes my specially modified version of QSopCast that can handle URLs.

---

### Post by MaindotC on 2008-02-21
That was a while ago - I got it working and in time for the game.  I installed Sopcaster which is much nicer.  Thanks for all your replies.

---

