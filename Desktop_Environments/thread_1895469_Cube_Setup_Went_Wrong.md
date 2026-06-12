---
title: "Cube Setup Went Wrong"
date: 2011-12-14
forum: Desktop Environments
---

### Post by TJP@WPI on 2011-12-14
Running Ubuntu 11.1 and Gnome.
 
Loaded CompizConfigSettings Manager.  Selected Desktop Cube. In the process Desktop Wall and Untiy got unselected.

Now when I go into this account there are no options to select, no tool bar, No time, Wifi or power indicator.

The only thing that show is File, Edit, View, History, Bookmarks, Tools, Help.

How do I get my account back to the way it was let alone how to make the cube work?

---

### Post by jimmydean886-2 on 2011-12-14
Man, what a legendary problem.

Fortunately, there is a simple way to do it.
Log out, then log back into ubuntu 2d (you can access that from the gear on your name selection on the login screen) then open the dashboard, and find compizconfig. Then, just reselect unity. The cube will be disabled, but Unity will work. Now sign back in to the "Ubuntu" session, and you're all set.

---

### Post by ksprasad on 2011-12-14
You can directly reset the unity by pressing Alt+F2 and typing:
 
unity --reset
 
If Alt+F2 did not work, then type it in a terminal.
 
Regards,
ksprasad

---

### Post by TJP@WPI on 2011-12-14
Ahh there it is.  I selected 2D on login and it is back.  That was E-Z.

Ok Now why doesn't the 3D cube work?

---

### Post by stinkeye on 2011-12-15
> **TJP@WPI said:**
> Ahh there it is.  I selected 2D on login and it is back.  That was E-Z.

Ok Now why doesn't the 3D cube work?
Because you are now in the 2d session which uses metacity and not compiz as the window manager.
There is a sticky at the top of this forum section - [URL="http://ubuntuforums.org/showthread.php?t=1892851"][B][U][COLOR="DarkRed"]Cube and Desktop Effects in Compiz
[/COLOR][/U][/B][/URL]

While your in the 2d session you may as well set compiz back to default. See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11538870&postcount=4")
Then login to the "ubuntu" session and follow the guide.

---

### Post by VanR on 2011-12-15
The answer I had was I ran the cube and used AWN. Of course Docky or Cairo-dock will work as well. That is the direction I take when I use Gnome 3.

---

### Post by stinkeye on 2011-12-15
> **VanR said:**
> The answer I had was I ran the cube and used AWN. Of course Docky or Cairo-dock will work as well. That is the direction I take when I use Gnome 3.

Yeah,really...good luck to you.

---

### Post by VanR on 2011-12-15
> **stinkeye said:**
> Yeah,really...good luck to you.

Well frankly I found that the cube and desktop effects are not friendly when running Gnome 3. You can get the effects with Gnome 3, but you lose Unity (yeah for that) or gnome-shell. At least that is my experience. So I find if I want effects on Gnome 3 I have to use a dock (Cairo-dock works well), which I prefer over either Unity or Gnome-shell anyway. To each his own. And BTW I am having good luck with it.

---

### Post by stinkeye on 2011-12-15
> **VanR said:**
> Well frankly I found that the cube and desktop effects are not friendly when running Gnome 3. You can get the effects with Gnome 3, but you lose Unity (yeah for that) or gnome-shell. At least that is my experience. So I find if I want effects on Gnome 3 I have to use a dock (Cairo-dock works well), which I prefer over either Unity or Gnome-shell anyway. To each his own. And BTW I am having good luck with it.

Sorry about the smart reply but I get sick of people coming into threads that your trying to give help on saying I switched to xfce , Unity is crap,
use this, use that, when usually the problem is conflicting compiz configs when they upgrade.Works fine until they load up ccsm.
Then the old configs come in to play.
I'm running the cube in unity on a fresh install with a few minor bugs but these bugs exist whether you have the unity plugin enabled or not.

---

### Post by jimmydean886-2 on 2011-12-15
What I had said before included restoring Unity 3d. The biggest problem I have ever had with 2d is that workspace settings didn't stick. Not a huge deal, and I'm not concerned because 3d is there. If you really want to run the full unity (which doesn't hide items when the launcher gets full, it just tilts them to save space) then go into CCSM (compizconfig) and select the unity plugin. Log out again, and log back in using the default "Ubuntu" option in the gear menu.

---

