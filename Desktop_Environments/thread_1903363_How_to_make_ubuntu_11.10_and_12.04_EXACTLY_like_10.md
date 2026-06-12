---
title: "How to make ubuntu 11.10 and 12.04 EXACTLY like 10.04"
date: 2012-01-02
forum: Desktop Environments
---

### Post by kangarooks on 2012-01-02
Hey folks

I managed to do what others only dreamt about :P I have taught my 11.10 to behave exactly like my good ol 10.04. You can now forget about the mess of Unity and Gnome Shell. Good ol classic gnome2 experience comming at ya, using gnome3 internals. This is how I did it, full comprehensive guide on my blog:
[URL="http://pleasanthacking.com/2012/01/02/making-ubuntu-11-10-and-12-04-behave-like-10-04/"]
[/URL]**[ 							[SIZE=1]Making Ubuntu 11.10 and Ubuntu 12.04 behave like Ubuntu 10.04						[/SIZE]]("http://pleasanthacking.com/2012/01/02/making-ubuntu-11-10-and-12-04-behave-like-10-04/")**

[SIZE=1] [/SIZE][URL="http://PleasantHacking.com/2012/01/02/making-ubuntu-11-10-and-12-04-behave-like-10-04/"]http://PleasantHacking.com/2012/01/02/making-ubuntu-11-10-and-12-04-behave-like-10-04/
[/URL]
:popcorn::KS:D

[IMG]http://pleasanthacking.files.wordpress.com/2012/01/screenshot-at-2012-01-02-043519-4wordpress.png
			  	 									 		 			[B]
[/B]

---

### Post by coffee412 on 2012-01-02
Very cool!

Thank you for all your effort! Ill be trying this soon.

BTW ----> 

[http://youtu.be/opsM3znflVw](http://youtu.be/opsM3znflVw)

:D

---

### Post by ajgreeny on 2012-01-02
Whilst I applaud your wish to move away from unity and all its problems, which I also find totally unusable, I have been led to understand that the **gnome-session-fallback** package, on which your ideas are based, is unlikely to remain available in the long term, perhaps not even for 12.04.  Do you have any other information on the long term situation for gnome-session-fallback?

I hope I have have got this wrong, and that it, or something else very similar to it, will remain a possible answer for those of us who love gnome, but are baffled by the unity/gnome-shell desktops.  If not I suppose it will mean a move to xfce, lxde, or even back to kde, which is where my linux story began, and before I even knew there were alternative DEs available.

---

### Post by kangarooks on 2012-01-02
Glad you liked it :) I'm sure many more will do as well :)

---

### Post by kangarooks on 2012-01-02
I think removing gnome-classic from ubuntu would be a silliest thing to do.

That package is backed by the Gnome3 team itself.
That package is in active development and uses gnome3 technology.
That package makes more good than bad, and people are actively supporting it with making new applets for it, to make gnome2 workflow alive

So i think its worthwhile to support this idea

---

### Post by ajgreeny on 2012-01-02
> **kangarooks said:**
> I think removing gnome-classic from ubuntu would be a silliest thing to do.

That package is backed by the Gnome3 team itself.
That package is in active development and uses gnome3 technology.
That package makes more good than bad, and people are actively supporting it with making new applets for it, to make gnome2 workflow alive

So i think its worthwhile to support this idea
I hope you are right about this.  Things may have moved on since I read that the fallback package was a temporary arrangement, and if it stays available it will save a large number of users from abandoning gnome completely.

Thanks for the update!

---

### Post by tomski on 2012-01-02
I already moved to xubuntu & now i've moved to openbox+cairo compmgr & cairo dock
have way much less resource used & more free drive space due to less libs for gnome etc

With all the options available to the linux user regardless of distro in use i find it pointless trying to battle to get the gnome you want.

Saying that i am keeping the mint dev fork of gnome2 in my peripheral vision just in case :)

i just cant stand unity/Gshell to me that kinda DE is perfect for a tablet but for a workstation is just horrid

IMO that is ;)

---

### Post by A_T on 2012-01-02
It would be great if Gnome could swallow their pride and continue to develop the classic style desktop alongside the shell. There does not seem to be a reason why this can't be done. For this user the shell just doesn't cut it as a desktop.

---

### Post by neu5eeCh on 2012-01-02
> **ajgreeny said:**
> I have been led to understand that the **gnome-session-fallback** package, on which your ideas are based, is unlikely to remain available in the long term, perhaps not even for 12.04.  Do you have any other information on the long term situation for gnome-session-fallback?

"There are no plans to remove gnome-session-fallback for Ubuntu 12.04 LTS Precise Pangolin, so if you use the GNOME Classic  session type in Ubuntu 11.10, there is no reason to think you will not  be able to use it in Ubuntu 12.04 LTS either. Currently, this release is  in alpha testing. gnome-session-fallback can be installed  in Precise systems, and if you have an Oneiric system with it installed,  it remains installed when you upgrade to the Precise alpha. If GNOME Classic  is the default session type in an Oneiric system (either globally or  for some user), it remains so when that system is upgraded to the  Precise alpha."

From [here]("http://askubuntu.com/questions/83334/will-12-04-default-into-unity-the-way-11-10-did").

And did you see the [Gnome Classic Mega Thread]("http://ubuntuforums.org/showthread.php?t=1873765")? You might want to add your blog link to the thread if you haven't already.

---

### Post by kangarooks on 2012-01-03
> **tomski said:**
> I already moved to xubuntu & now i've moved to openbox+cairo compmgr & cairo dock
have way much less resource used & more free drive space due to less libs for gnome etc

With all the options available to the linux user regardless of distro in use i find it pointless trying to battle to get the gnome you want.

Saying that i am keeping the mint dev fork of gnome2 in my peripheral vision just in case :)

i just cant stand unity/Gshell to me that kinda DE is perfect for a tablet but for a workstation is just horrid

IMO that is ;)

Each to their own :) 

I like things as COTS / stock as I can, especially now so I dont have to engage with puters much but get on with my life into a Remedial Masseur course. And i really liked my gnome2 workflow, so after half day of tweaks I came up with something that met my needs, that is based on actively supported system, and I chose to share it with others.

---

### Post by kangarooks on 2012-01-03
> **VTPoet said:**
> 
And did you see the [Gnome Classic Mega Thread]("http://ubuntuforums.org/showthread.php?t=1873765")? You might want to add your blog link to the thread if you haven't already.

snip

That said, i think you can post links to this thread, but I have other things to do with my life now. If you wanna spread around this fix who am i to stop you? :P

---

### Post by u2nTu on 2012-01-03
Trying desperately to love (or at least 'like') the Unity interface. But still have not found a way to get [running app icons to appear on the panel]("http://ubuntuforums.org/showthread.php?t=1873519").

Adding this thread to my watchlist. If no improvement in 12.04, will give this method a try. Sometimes progress is regressive.

---

### Post by kangarooks on 2012-01-04
There was a slight stuffup. Wordpress rearanged on its own code segments that were in list, so the effect was total mess. Now it is fixed, if there are some other potential prolems let me know whats going on. 

Thanks!

---

### Post by kurt18947 on 2012-01-04
> **u2nTu said:**
> Trying desperately to love (or at least 'like') the Unity interface. But still have not found a way to get [running app icons to appear on the panel]("http://ubuntuforums.org/showthread.php?t=1873519").

Adding this thread to my watchlist. If no improvement in 12.04, will give this method a try. Sometimes progress is regressive.

I agree about quick switching between open apps/windows.  I use and prefer gnome-shell to Unity though both work.  I have tint2 (found in the repositories) in my startups. It adds a bottom bar to Unity & Gnome Shell and lists open windows.  Click to switch;).  Another possibility in Shell is an extension to do the same thing and also display a workspace switcher a la Gnome 2.

---

### Post by u2nTu on 2012-01-04
Had found tint2 before, but I have a 23" monitor with loooong stretch across the top panel that's unused. Blank. Nothing there.

Seems like a big waste.

Some report getting active app icons to appear there, but no combination of settings I've found works for me. Really want this.

---

### Post by kangarooks on 2012-01-09
> **u2nTu said:**
> Had found tint2 before, but I have a 23" monitor with loooong stretch across the top panel that's unused. Blank. Nothing there.

Seems like a big waste.

Some report getting active app icons to appear there, but no combination of settings I've found works for me. Really want this.

i use one floating gnomepanel there, that is set to autohide, with autohide time very long, its called wing panel conversion, its somewhere on teh net, cant point it more acurately now, but i use it like so in my 11.04 that i got back to. in my 11.10 conversion i also use it like that, but i have to launch that panel preferences to keep it from autohiding at start...

---

### Post by kangarooks on 2012-01-20
> **u2nTu said:**
> Had found tint2 before, but I have a 23" monitor with loooong stretch across the top panel that's unused. Blank. Nothing there.


i used exactly this solution on my desktop:

[http://www.omgubuntu.co.uk/2010/12/create-a-wingpanel-effect-using-the-default-gnome-panel/](http://www.omgubuntu.co.uk/2010/12/create-a-wingpanel-effect-using-the-default-gnome-panel/)

it covers up the top bar with the gnome panel, which is nice :)

---

### Post by daldude on 2013-01-21
Now if you could find a way to now make it look like 10.04 with the Mac Leopard Theme installed that would be even better.:D

---

### Post by u2nTu on 2013-01-25
@daldude, since your post revived this old thread, guess it's a good time to update that I've found a solution: abandon Unity.

Been running for quite some time now with Gnome - No Effects. Very happy. If Canonical persists with Unity, this solution will be permanent for me. :p

---

