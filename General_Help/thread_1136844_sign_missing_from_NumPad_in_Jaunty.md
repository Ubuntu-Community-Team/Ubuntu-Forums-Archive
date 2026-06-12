---
title: "* sign missing from NumPad in Jaunty"
date: 2009-04-25
forum: General Help
---

### Post by eyerouge on 2009-04-25
After the upgrade to Jaunty the *-sign isn't shown/written when I hit the *-key on my numberpad. Instead of * a &#8901; (weird dot) appears. 

I've checked my keyboard layout settings and haven't changed anything in them since they're correctly setup(?). They use a generic 105&#8722;key international keyboard and Swedish for language. The problem remains even if I change language. While here, I'm also wondering if I need to reboot the computer or restart the user session for changes in keyboard modell to take place in the Keyboard settings.

I've also checked my xorg setup and it has the following:

```

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"se"
#EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

```

As you can see the update to Jaunty commented out all the keyboard stuff, and I put it back in without any success of solving my * problem.

Keyboard modell is: (HP) SK-2960

Edit 2: Solved problem, according to the following:

[[img]http://www.ubuntu-pics.de/thumb/12981/screenshot47_U9z334.png[/img]](http://www.ubuntu-pics.de/bild/12981/screenshot47_U9z334.png)

---

