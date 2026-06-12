---
title: "Gnome3 - Firefox icon keeps going generic"
date: 2011-05-03
forum: Desktop Environments
---

### Post by ratcheer on 2011-05-03
On my main Ubuntu Natty installation running Gnome3 and  gnome-shell, my Firefox icon keeps turning to a generic icon. Yesterday,  I fixed it by changing my icon theme from adwaita to unity-icon-theme,  logging off, and logging back on. However, I had to reboot this morning,  and the Firefox icon was back to generic, again. How can I fix the icon,  permanently?

I have not had this problem on my Natty testing installation.

Thanks,
Tim

---

### Post by ratcheer on 2011-05-03
Installing the Faenza icon theme seems to have resolved the problem, but I need to reboot to be sure.

Tim

---

### Post by ratcheer on 2011-05-03
Ok, the fix survived at least one reboot. For now, I am assuming that the problem is resolved.

Tim

---

### Post by ratcheer on 2011-05-04
I rebooted again today and the icon went generic on me, again. :(

Tim

---

### Post by 23dornot23d on 2011-05-04
Can you give us some screen shots ..... so we can see exactly what is happening .....



With a screenshot of the icon you want to be permanent  .......


Almost sounds as if your configuration keeps getting reset ....... for some reason .....
but if its one icon ...... that seems odd.

---

### Post by ratcheer on 2011-05-04
Here is a screenshot of my first screen of applications. See how the Firefox icon is like a purple diamond or something. As the correct icon is now gone, I can't show the one I expect to have.

Tim

---

### Post by ratcheer on 2011-05-04
PS - I don't think it is even using the Faenza icons anymore, even though the Tweak Settings app says it still is.

Tim

---

### Post by 23dornot23d on 2011-05-04
You look as if you need the Themes loading in .....

There is a extra box shown where it says 

Window Applications
then it should display  Themes ..... as in my screenshot  [**[COLOR=Red]LINK[/COLOR]**]("http://img192.imageshack.us/img192/1728/screenshot12ix.png")

Another [**[COLOR=Red]Sceenshot[/COLOR]**]("http://img84.imageshack.us/img84/3417/screenshot13sw.png") ...

[**[COLOR=Red]THEMES SCREENSHOT[/COLOR]**]("http://img146.imageshack.us/img146/6946/screenshot14o.png")

Looks like the Themes need s loading in as you say ...... have some instructions in my link
below ...... under Gnome-Shell

or go to this site ..... [MUSINGS THEME SELECTOR]("http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html")

---

### Post by ratcheer on 2011-05-04
Sorry, I don't see what you mean.

Tim

---

### Post by 23dornot23d on 2011-05-04
I have added another screenshot in my last post .... will also do a closer view of the part thats
not showing on your screenshot ..... in a moment


[IMG]http://img508.imageshack.us/img508/5945/themes.jpg[/IMG]


There have been some updates ...... UGR may have this included now ..... if not
I have instructions in my link that work ..... for this ..... plus links to the debian files that you need
to complete it ........

Will add here to keep it all available ..... for others to use ..... some do not like clicking links,

These are the things that worked on 3 of my systems ....


_________________________________________

[Extensions]("http://cid-32ec6e89f4aa803b.office.live.com/browse.aspx/Linux?wa=wsignin1.0&sa=168264950") .... 
posted by [Cbowman57 on this thread in Ubuntu forums]("http://ubuntuforums.org/showthread.php?p=10753298#post10753298")
it works too using gdebi from the terminal .... 

sudo apt-get install gdebi-core

Then enter in a terminal ....... 
( for the two files that you need first - check the thread above for my full instructions )

sudo gdebi (filename)

has you have to answer yes ....
when installing them ......

Full list of [Gnome Shell Extensions and what they do ]("http://live.gnome.org/GnomeShell/Extensions")...
____________________

---

### Post by ratcheer on 2011-05-04
Things are getting curiouser and curiouser.

I installed the latest updates using aptitude (update, then safe-upgrade). Then I rebooted. The option to login to the gnome-shell was gone. The option to login to Ubuntu would not work. The only other option was to login to a recovery console. Luckily, that worked.

I showed package gnome-shell and it was gone. I took a wild shot and installed it. It was installed along with a lot of other packages (maybe about 30 in all). Then I rebooted again.

I am logged back in to gnome-shell. Also, my Faenza icon them is back in place and active.

Unfortunately, at this point, I have little faith that things will remain good.

Tim

---

### Post by 23dornot23d on 2011-05-04
I run Gnome-shell on 3 of my systems all have themes on them and all are running well
even my 7 year old laptop ..... 

Do you want to install the Themes ?

These [2 files need to be installed]("http://cid-32ec6e89f4aa803b.office.live.com/browse.aspx/Linux?sa=835391266") using gdebi , to start with.


[[COLOR=Red]SCREENSHOT[/COLOR]]("http://img151.imageshack.us/img151/2541/screenshot15d.png") ON MY SYSTEM SHOWING THE TWO FILES TO DOWNLOAD AND THE VERSIONS

[File 1]("http://kmzipq.blu.livefilestore.com/y1prqhpljgFPs5yI3ADiW7a-UqSFwmpoLiSOW_k9uSCsrZN6In4GZy1_gCfSiLc0MA5JsR_pL4qvv4mzkMiiLB-LA/gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb?download&psid=1")

[File 2]("http://kmzipq.blu.livefilestore.com/y1ppk5e7EYl7JhCkgEwuph8P6BtabFjMjNTetoURgGzHExsrapNtIdr174qf7WGWI022db8no3ONuuj1-ujiyGuIA/gnome-shell-extensions-common_3.0.1-2_all.deb?download&psid=1")


I can go through step by step .....

> 
Unfortunately, at this point, I have little faith that things will remain good.
You sound worried that doing these two commands broke your system in some way ...

aptitude (update, then safe-upgrade) not sure why though >>>> yet ?

Is there a problem now ...... ?

Error messages ?

[COLOR=Red]Seems to me from your screenshot[U]

[/U][/COLOR]  			 				 					Attached Thumbnails 					 					 [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=191156&stc=1&thumb=1&d=1304556429[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=191156&d=1304556429")    					
 				 			  			  			  			  			  			

[COLOR=Red][U]
[/U]the problem is solved ..... [/COLOR]

---

### Post by ratcheer on 2011-05-05
I thought about your questions overnight.

I doubt that I will install the Gnome shell extensions. I like to keep my installations simple, clean, and maintainable. I read in one of the links you posted that even the gnome shell developers don't think the shell extensions are the way forward. [http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html](http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html)

I am certain that the safe-upgrade removed gnome-shell. I was running it when I ran the update and safe-upgrade, then it was not installed after I finally got rebooted.

Finally, yes, it does *seem* like my problem is solved, but it also seemed like that after I first installed Faenza and rebooted (post #3). But later, the problem happened, again.

I really do appreciate your help, for which I thank you very much.

Tim

---

### Post by 23dornot23d on 2011-05-05
> 
Finally, yes, it does *seem* like my problem is solved, but it also  seemed like that after I first installed Faenza and rebooted (post #3).  But later, the problem happened, again.

I really do appreciate your help, for which I thank you very much.


Ok cheers - your welcome .

---

