---
title: "Gutsy Final: how do I *completely* get rid of the brown screen shown during login"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by ariel on 2007-10-20
Hi, I've been using 7.10/gutsy final for a couple of days now, after a fresh install. It definitely is the best distro ever so far. Now the only major annoyance I'm experiencing is, I cant get rid of the the brown screen shown right after the GDM Login window (I really really dislike Ubuntu brown-fixation thingy).

Typically in the past, doing:

   - System-->Administration-->Login Window
         then selecting a non-brownish login, then selecting "Background Color" to the color I like (black shades, at the moment :)

   And  then doing:

    System-->Preferences-->Desktop Background, then selecting my non-brownish background 

... would fix the "brown fixation problem" :).  The problem with Gutsy is, 
after doing all this, a brown screen is still shown for a few seconds right after the GDM Login succeeds, and before switching to my chosen background.

 I know that perhaps installing a non-official U-splash theme may help, but I want to avoid this if at all possible (trying to avoid installing non-official packages if possible, to ease the next update...)

Thanks!!

---

### Post by Druke on 2007-10-20
I'm having this same problem actaully

---

### Post by kshane on 2007-10-20
You have to change the login splash, etc.. Loads before the desktop...

Kevin

---

### Post by Druke on 2007-10-20
I've done that, and the color is changed as well.

---

### Post by kshane on 2007-10-20
> **Druke said:**
> I've done that, and the color is changed as well.

Isn't color change following the splash whjat you're talking about?

Kevin

---

### Post by NoVista on 2007-10-20
I have your fix:
The problem is at /etc/gdm/PreSession/Default.

Try mine ..

---

### Post by ariel on 2007-10-20
Awesome, thanks NoVista, you fixed it. I think this is a bug.... did you file a bug in launchpad or should i do it :)

---

### Post by NoVista on 2007-10-20
No, I din't file a bug. 
Is it?
Feel free if you wish. You can compare my file to the default to see what's changed.

---

### Post by secular on 2007-10-23
Thanks, NoVista. I used your file and no longer see the brown--not that there's anything wrong with the brown! :wink:

---

### Post by subrosa on 2007-10-23
The way I did it, instead of using the zip file that is attached is to :

vim /etc/gdm/PreSession/Default

Scroll all the way to the bottom and find this little block of code :

# Default value
        if [ "x$BACKCOLOR" = "x" ]; then
                BACKCOLOR="#000000"
        fi

I already changed mine, but #000000 is black, the ugly tan has a d in the hex value. 

It seems like it fails to grab the color from the gdm theme, not sure if it is a "bug" or just something you have to change if you really hate tan. 

-Paul

---

### Post by FuturePilot on 2007-10-23
> **ariel said:**
> Awesome, thanks NoVista, you fixed it. I think this is a bug.... did you file a bug in launchpad or should i do it :)

Already been reported
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/132833]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/132833")

---

### Post by stekker on 2007-11-05
Nice colorpatch but is absolutely NO BUGFIX.!!

You see, the camelcolor you always get is a result of failed authentication of gdmflexiserver which is the REAL bug.

The camelcolor can thus be seen as a kind of error-report.
Patching the color just covers up the real bug.

If the authenticationproblem of gdmflexiserver is fixed (bit of a problem because GTK deliberately refuses setuid or setgid which is the correct way to prevent security issues), the color of your choise will be nicely set by gdmsetup (i.e. by the value in gdm.conf-custom) as it should be, 

anyway, here is my gdm log (~/.xsession-errors), pay attention to the gtk-warnings because they'll tell you much about what is REALLY happening.
-----------------------------------------------------------------------------------

+ gdmwhich xsetroot
+ COMMAND=xsetroot
+ OUTPUT=
+ IFS=:
+ test -x /usr/bin/xsetroot
+ test x = x
+ OUTPUT=/usr/bin/xsetroot
+ test -x /sbin/xsetroot
+ test -x /usr/sbin/xsetroot
+ test -x /bin/xsetroot
+ test -x /usr/bin/xsetroot
+ test x/usr/bin/xsetroot = x
+ test -x /bin/xsetroot
+ test -x /usr/bin/xsetroot
+ test x/usr/bin/xsetroot = x
+ IFS= 	

+ echo /usr/bin/xsetroot
+ XSETROOT=/usr/bin/xsetroot
+ [ x/usr/bin/xsetroot != x ]
+ CHECKBACKCOLOR=OK
+ [ xTHEMED = xTHEMED ]
+ gdmflexiserver -a --command=GET_CONFIG greeter/GraphicalThemedColor :0

(process:5975): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
+ BACKCOLOR=
+ echo
+ sed s/^\([^ ]*\) .*$/\1/
+ CHECKBACKCOLOR=
+ [ x = xOK ]
+ BACKCOLOR=
+ [ x != xOK ]
+ gdmflexiserver -a --command=GET_CONFIG greeter/BackgroundType :0

(process:5979): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
+ BACKTYPE=
+ [ x = xOK 1 ]
+ [ x = xOK 2 ]
+ [ x = x ]
+ BACKCOLOR=#dab082
+ /usr/bin/xsetroot -cursor_name left_ptr -solid #dab082
+ exit 0

----------------------------------------------------------------------------------------------------------------

---

### Post by ariel on 2007-11-06
Understand. I also see the launchpad bug mentions this. 

We got rid of the brownish tan camelcolor, but now I wonder what's the consequence of gdmflexiserver not initializing? I don't seem to notice problems in my everyday desktop use.

---

### Post by markharding557 on 2007-11-07
> **subrosa said:**
> The way I did it, instead of using the zip file that is attached is to :

vim /etc/gdm/PreSession/Default

Scroll all the way to the bottom and find this little block of code :

# Default value
        if [ "x$BACKCOLOR" = "x" ]; then
                BACKCOLOR="#000000"
        fi

I already changed mine, but #000000 is black, the ugly tan has a d in the hex value. 

It seems like it fails to grab the color from the gdm theme, not sure if it is a "bug" or just something you have to change if you really hate tan. 

-Paul

An easy way to get any colour you want is to bring the desktop colour changer up and click colours tab select a colour and copy its number and paste it here 
# Default value
        if [ "x$BACKCOLOR" = "x" ]; then
                BACKCOLOR="#colournumber"

---

### Post by Smbrandes on 2007-12-05
A note for the novice linux types. when editing the code you can use the arrow keys to get around, nad more importantly press the insert key to add text and the delete key to remove text. Funny how straightforward it al is once you know the funny little details.

---

### Post by Fruhwirth on 2008-01-25
> **stekker said:**
> Nice colorpatch but is absolutely NO BUGFIX.!!

You see, the camelcolor you always get is a result of failed authentication of gdmflexiserver which is the REAL bug.

The camelcolor can thus be seen as a kind of error-report.
Patching the color just covers up the real bug.


Perhaps so, but this gdmflexiserver bug doesn't cause me any problems, so I'm just find with only treating the symptom of an unfixed, underlying bug. 

Thanks NoVista.

---

### Post by chokas on 2008-01-31
> **NoVista said:**
> I have your fix:
The problem is at /etc/gdm/PreSession/Default.

Try mine ..

Thanks for the patch!

Although there shouldn't be a reason to replace the file or edit the line =S...

---

### Post by KingWilliam on 2008-02-12
```

# Default value
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#000000"
fi

```

if you comment these lines (place a '#' in front of them) the ugly brown screen will have the color you have chosen in the settings as background of your login screen.

---

### Post by firefeather on 2008-04-30
This is now fixed in Hardy. Hooray! :)

---

