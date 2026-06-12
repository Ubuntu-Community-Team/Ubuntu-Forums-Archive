---
title: "JWM in Ubuntu"
date: 2010-05-02
forum: Desktop Environments
---

### Post by Ylon on 2010-05-02
I am try to use this very light and fast DM for Ubuntu. Combined with pcmanfm it's the ultimate tool for having my Lucid Lynx really fly. Now, I've just some two little problem I would find a solution in order for keep this as regular desktop. These:
sudo apt-get install jwm pcmanfm menu
are the three packages I am using for have a complete desktop (pcmanfm take the task to draw icons and wallpaper in the background)
Now, my problem is: 


whatever I put in the ~/.jwmrc I lost the debian menu. What I had to put in the .jwmrc file in oder to keep it (my settings *and* debian menu)?

---

### Post by cariboo on 2010-05-02
This is a support request. moved.

---

### Post by chris4585 on 2010-05-07
bump... since this thread is only 5 days old and I'd also like to know....

thanks

---

### Post by kerry_s on 2010-05-07
been along time since i used jwm, but i think you would use the "**<Include>/etc/xdg/menus/debian.menu</Include>**"

did you read the man page? (**man jwmrc**)

---

### Post by chris4585 on 2010-05-07
> **kerry_s said:**
> been along time since i used jwm, but i think you would use the "**<Include>/etc/xdg/menus/debian.menu</Include>**"

did you read the man page? (**man jwmrc**)

It appears the man for jwmrc doesn't exist.  I tried your suggestion but it didn't work for me, I probably didn't add it in the config right..  I looked in /etc/menu-methods a bit, and decided to just use the default jwmrc it gave me.  Thanks

---

### Post by kerry_s on 2010-05-07
> **chris4585 said:**
> It appears the man for jwmrc doesn't exist.  I tried your suggestion but it didn't work for me, I probably didn't add it in the config right..  I looked in /etc/menu-methods a bit, and decided to just use the default jwmrc it gave me.  Thanks

maybe it's "**man jwm**"?

---

### Post by Ylon on 2010-05-08
This is the "menu" part in my ~/.jwmrc
```
    <RootMenu height="15" onroot="123">
       <Program icon="rxvt.png" label="Terminal">x-terminal-emulator</Program>
          <Program icon="firefox.png" label="Www Browser">x-www-browser</Program>
         <Separator/>
            <Include>/etc/xdg/menus/applications.menu</Include>
            <Include>/etc/xdg/menus/gnomecc.menu</Include>
            <Include>/etc/xdg/menus/settings.menu</Include>
         <Separator/>
       <Restart label="Restart" icon="restart.png"/>
       <Exit label="Exit" confirm="true" icon="exit.png"/>
       <Program label="Shutdown" confirm="false" icon="exit.png">
         /usr/lib/jwm/jwm-poweroff.sh
      </Program>
    </RootMenu>
```
The field between the separator are just empty

---

### Post by Ylon on 2010-05-10
Still interested for the solution.

---

### Post by Salix0210 on 2010-05-19
The /usr/share/doc/jwm/README.Debian file says:

"There is no automatic configuration which would add programs to the
menus. Edit /etc/jwm/jwmrc or copy it to personal ~/.jwmrc startup file."

But /usr/share/doc/menu/examples/ has some interesting stuff...

---

### Post by Ylon on 2010-05-20
Well, I did notice that the "menu" package (**sudo apt-get install menu**) keep update all kinds of menu among all DekstopManager (JWM included).
Sadly, the menu package update only the file /etc/jwm/jwmrc and ignore my ~/.jwmrc.

It's there a way to make a easy script to put all stuff <rootmenu>...</rootmenu> in /etc/jwm/jwmrc and substitute the one in my ~/.jwmrc?
(or maybe set *menu package* to manage my personal settings)

jwm+pcmanfm (who manage the desktop also) is the perfect lowpower solution...the only thing that bore me is to update manually the menus)

---

### Post by XubuRoxMySox on 2010-05-20
The newest version of Puppy Linux is [built on minimal Ubuntu Lucid]("http://bkhome.org/blog/?viewDetailed=01595")! It uses JWM. You might have a look at it and see how they did it.

Enjoy,
Robin

---

