---
title: "Broken Compiz-aiglx after upgrade today"
date: 2006-08-25
forum: Desktop Environments
---

### Post by wvelez on 2006-08-25
Hi guys,

After running an system upgrade today I lost the window frames when running Compiz.  I have to manually switch to Metacity in order to have them.  

Compiz-aiglx has been running flawlessly on my laptop for the last 4 months.  

My video card is:  Intel Corporation 82852/855GM Integrated Graphics Device (rev 02).

Can anyone help me undo the upgrade?

Thanks a bunch.

Regards,
-will

---

### Post by qamelian on 2006-08-25
I'm have a somewhat different problem after today's updates.

The latest updates to Compiz, cgwd, and dri modules seems to be causing a weird display problem on my system. Basically, what I'm getting is a blank white background instead on my selected wallpaper. The top and bottom panels appear although they also appear blank and white. No icons appear on the desktop while compiz is running. If I mouse over appropriate parts of the top panel and click, blank, white menus appear. Navigating the menus displays blank, white sub-menus.

Notice a theme here? I can click in menus (albeit blindly) to launch applications, or I can alt-F2 to launch a blank white run box and type a command here to launch an application. None of the text I type is displayed. Any applications that are launched are also blank and white except that the cgwd theme I've selected appears. Finally, if the apllication I launch is gnome-terminal, the terminal window works just fine; everything in the terminal windows displays and works as expected.

If I switch from compiz to metacity by typing      Code:
     [LEFT]metacity --replace[/LEFT]
  
 in the run box, everything displays fine.

Compix/AIGLX was working fine for me before today's update.

Any ideas? Anyone else experiencing this?:confused:

---

### Post by raggit on 2006-08-26
Exact same problem

---

### Post by PathSpace on 2006-08-26
Grrrr...I am having the EXACT same problems as the person who started the thread.  The only way I can even get window decorations is to run "metacity --replace".  :|  Also, I get no Compiz effects either.

---

### Post by defeca on 2006-08-26
The same problem here!!!

---

### Post by Uncle Spellbinder on 2006-08-26
All working perfectly here after updating early this morning.

Installed Compiz Components:

*compiz* 0.0.13.39-0ubuntu1
*compiz-core* 0.0.13.39-0ubuntu1
*compiz-gnome* 0.0.13.39-0ubuntu1
*compiz-quinn-aiglx* 0.0.13-0ubuntu5
*compiz-plugins* 0.6-0ubuntu1
*gset-compiz* 0.3.4-3v1ubuntu3
*cgwd* 0.61-0ubuntu1
*cgwd-themes* 0.14-0ununtu1

---

### Post by PathSpace on 2006-08-26
Maybe it's because I am using the vanilla packages...  :(

---

### Post by elvislu on 2006-08-26
I have no packages like compiz-quinn-aiglx. I only got vanilla packages. What's the repository?

---

### Post by Uncle Spellbinder on 2006-08-26
> **elvislu said:**
> I have no packages like compiz-quinn-aiglx. I only got vanilla packages. What's the repository?

I'm using 

```
*deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx*
```

---

### Post by qamelian on 2006-08-26
> **Uncle Spellbinder said:**
> All working perfectly here after updating early this morning.

Installed Compiz Components:

*compiz* 0.0.13.39-0ubuntu1
*compiz-core* 0.0.13.39-0ubuntu1
*compiz-gnome* 0.0.13.39-0ubuntu1
*compiz-quinn-aiglx* 0.0.13-0ubuntu5
*compiz-plugins* 0.6-0ubuntu1
*gset-compiz* 0.3.4-3v1ubuntu3
*cgwd* 0.61-0ubuntu1
*cgwd-themes* 0.14-0ununtu1

Unfortunately, the Quinn packages don't seem the like the ATI Mobility 9000 in my laptop. The vanilla packages work fine, but the Quinn packages run so slow for me they are unusable.:(

---

### Post by PathSpace on 2006-08-26
This is so #%$&! annoying; between this and trying to fix it (very unsucessfully) my system has gotten into such poor shape that I am gonna have to re-install Ubuntu.  ](*,) ](*,) 

This stinks.  Any advice on how to install Compiz after I re-install Ubuntu?  I have the 1810 type card.  Thanks in advance for any advice.

---

### Post by fibertek on 2006-08-26
Yea I had the same issue... no compiz.. i completely removed and reinstalled compiz-vanilla, compiz-vanilla-aiglx etc etc.. works ok except now CGWD doesnt work at all.. so i have no menu bars now.. anybody have any ideas on that one? i have tried downgrading to cgwd 0.59 just to see what happens adn i get the same results.. please help!! i just got compiz working the way i liked it yesterdya and now this!!! :)

---

### Post by defeca on 2006-08-26
I had the same problem. Then, following this link:

[http://ubuntuforums.org/showthread.php?t=145068&page=132]("http://ubuntuforums.org/showthread.php?t=145068&page=132")

I did:

```
sudo apt-get install cgwd compiz compiz-core compiz-gnome xserver-xorg-air-core
```

 I removed the gset-compiz, and installed gnome-compiz-manager 

```
sudo apt-get install gnome-compiz-manager
```

Here it's working now.

---

### Post by fibertek on 2006-08-27
AHA! figured it out...vanilla no longer works more or less b/c it needs gset-compiz.. so i went back to compiz-core/compiz-gnome etc using gnome-compiz-manager (running compiz-tray-icon from CLI) and working OK now :)

---

### Post by PathSpace on 2006-08-27
YES!  It not only works, but actually is even slicker now!  Thanks!  :D

---

