---
title: "HOW TO:  1-player Pioneers, local game (Settlers of Catan)"
date: 2009-12-19
forum: Gaming &amp; Leisure
---

### Post by TokyoYank on 2009-12-19
**EDIT (update for 10.04)**

It works, no CLI required, thanks to firmit[LIST]
[*]Applications > Games > Board > Pioneers
[*]Create game
[*](Pioneers Server starts) > Start Server
[*]Add Computer Player (3 times)
[*](back to the Start a new game window) Join a private game
[*]OK.   ... enjoy!
[/LIST]


_Original post follows, for those running 9.10-ish  .  .  .  .  .  ._

OK, for the benefit of other Settlers newbies out there, I happily report how I got a single player game with 3 computer AI opponents to work, using the "pioneers" packages.  (**Search "settlers" in Synaptic and install all packages starting with pioneers**)

my goal[LIST]
[*]Start a game locally[LIST][*]Securely, no ports open to the outside[*]Privately, not listed on a meta-server anywhere[/LIST]
[*]Have 2-3 computer players [/LIST]

Did I succeed?  I have updated ubuntu9.04 64bit and pioneers 0.12.2

==> Could someone kindly confirm for the lastest ubuntu (9.10 at the time of writing) when you post?


Summary:  It seems like the problem is somehow the name "localhost" is not recognized as 127.0.0.1, so this must be entered manually

-------------------------

Edit:  A good option for beginners seeking a good tutorial, or for a 1P game with good AI, check out [the official Settlers online play website]("http://www.playcatan.com/").  (Credit to [IndyAero's post]("http://ubuntuforums.org/showpost.php?p=8533375&postcount=12"))

-------------------------

"How I Did It" (**HOW TO** in bold)

[LIST][*]**Start the Pioneers Server**, Applications > Games > Pioneers Server[LIST]
[*]The default settings look fine, except for Server Parameters[LIST]
[*]**uncheck "Register server"**[/LIST][/LIST]
[*]**Click "start Sever"**[LIST][*]a Running Game tab opens.  However, only 1 of 3 buttons works as intended.  Here's what they do, and how to fix them using new terminal windows[LIST][*]Launch Pioneers Client[LIST][*]BROKEN: As reported in threads the past year, a window pops up but does not connect.  An error window appears too briefly to display or read.
[*]FIX:  **start Pioneers manually**, Applications > Games > Pioneers.  (or, if you like from a new terminal, enter:  pioneers)[LIST][*]"Start a new game" dialog appears, **click "Join private game"**[*]Server Host **127.0.0.1**[*]Server Port 5556 (or whatever you entered before)
[*]=> A new line should appear in the Pioneers Server window as a connected player
[*]=>The Pioneers client looks promising, displays a game board, but no buttons can be clicked yet.  At least you can read Help, woo hoo[/LIST][/LIST]
[*]Add Computer Player[LIST][*]BROKEN: A new line appears, new name, however the Location is "not connected" and the Number is "-1"
[LIST][*]==> If you started pioneers-server-gtk in the terminal, the following error appears:
ai port is 5556
12:11:01 - Type of computer player: greedy
12:11:01 - Connecting to localhost, port 5556
12:11:01 *ERROR* Error connecting to host 'localhost': Connection refused[/code]
[*]This happened no matter what port I tried[/LIST]
[*]FIX: At a **new terminal**, Applications > Accessories > Terminal, enter  pioneersai -n comp1 -s 127.0.0.1[LIST][*]=>A new line in the Pioneers Server window should appear, with name "comp1".  (You can change "comp1" to whatever is more interesting to you, as you like.)[*]Do this same step 2 more times[LIST][*]or, FIX: TO ENTER ALL 3 AI AT ONCE: open a terminal, **copy and paste this one** big mondo mama-jamma **line**, then minimize the terminal window```
pioneersai -n comp1 -s 127.0.0.1 & pioneersai -n comp2 -s 127.0.0.1 & pioneersai -n comp3 -s 127.0.0.1 &
```
[/LIST][/LIST][/LIST][/LIST][/LIST][/LIST]

At this point, the game starts.  Enjoy.

_NOTE: _ The default port, 5556, is listed in /etc/services as the port for freeciv.  So it's probably a good idea:  **don't run freeciv at the same time**.

---------------

Please post any corrections, and I'll edit this How-To.  Cheers

---

### Post by fishexe on 2009-12-21
This is still a problem with Pioneers in Ubuntu 9.10.  I wonder if the upstream maintainers know about it?  It seems very obnoxious because all the buttons and fields in the GUI default to localhost, not 127.0.0.1, even though they're supposed to be the same thing.

---

### Post by TokyoYank on 2009-12-21
'localhost' vs '127.0.0.1' ==>  Any coders have any ideas how/why this is getting mangled?


Anyone ==> in my browser, the How-To seems too wide, with horizontal scrolling.  Do you see that?  Any way to fix it?

*OP Edit notes:  added link to Settler's free authentic web play*

---

### Post by onesojourner on 2009-12-21
Thanks a bunch. I did not even know there was a settlers game that you could play with ubuntu.

---

### Post by bonkey on 2010-01-05
I had this problem, the issue was that there is a localhost entry in IPV6 section of the /etc/hosts file.

The fix was to change:
::1    localhost ip6-localhost ip6-loopback

to this:

::1     ip6-localhost ip6-loopback


Not sure if this is the "real" solution or if it breaks anything in IPV6, but it fixed my pioneers issue.

---

### Post by rodmacpherson on 2010-02-02
That is the solution. 

My ubuntu 9.10 install has the localhost problem, my xubuntu 8.04 install does not.

8.04 has:

::1  ip6-localhost ip6-loopback

127.0.0.1 localhost

---

### Post by mlabowicz on 2010-04-11
Any idea if this will get fixed in 9.10 or 10.04? I'd hate to have to make this update every time I upgrade my Ubuntu :)

---

### Post by Punkristo on 2010-07-23
There's a free Settlers of Catan online version for Linux/Mac/Win at [http://www.playcatan.com/](http://www.playcatan.com/)

---

### Post by firmit on 2010-08-02
I just installed, unchecked register server - and used the server to start the client. Everything worked for me without using cli.
Ubuntu 10.04 LTS

---

### Post by rodmacpherson on 2010-08-25
> **Punkristo said:**
> There's a free Settlers of Catan online version for Linux/Mac/Win at [http://www.playcatan.com/](http://www.playcatan.com/)

 I hate to say it, because I am a huge fan of the board game and would love to support the company's market research that I'm sure they get from this, but Pioneers is much better.   First of all, I've had fewer problems getting Pioneers to work on Linux. Secondly, I played with the playcatan version for a while and never figured out how to specify who i wanted to play with. Sure, joining a random game was easy enough, but if I wanted to play with my wife and a friend, not so simple. Thirdly I find the interface of Pioneers to be much cleaner and easier on the eyes. And finally, Pioneers takes fewer system resources to run.

---

