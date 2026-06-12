---
title: "Load at Startup"
date: 2011-03-14
forum: Desktop Environments
---

### Post by shafiekd on 2011-03-14
Hi

I'm a newbie to Ubuntu, so please excuse any ignorance.

I have Ubuntu 10.04 LTS installed on my HP Compaq Presario CQ60.
Unfortunately the screen is busted & I'm using an external LCD.

It boots directly onto the LCD, but the resolution is 800x600 by default, the only other option is  640x480.

I'm assuming its using the VESA drivers for the graphics.

I've managed to temporarily fix the resolution to 1024x768 by running the following in terminal for every session:
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr --addmode VGA1 1024x768_60.00
xrandr --output VGA1 --mode "1024x768_60.00"

I've added a document to /etc/init.d so that it may be loaded on startup, but it does not seem to work.

Does anyone know how i can make this load at startup?

Thanks

---

### Post by Copper Bezel on 2011-03-14
Under Preferences, there's an item titled Startup Applications. When you add the script, just put the path to your script as the "command" and select "Application" rather than "Application in Terminal."

There's probably a more permanent solution to this problem, but I like your approach. = )

---

### Post by cipherboy_loc on 2011-03-14
Don't you have to run xrandr with sudo or as root? If you can run it as a regular user, follow Copper Bezel's method. Else, you should use init.d scripts.


Cipherboy

---

### Post by Copper Bezel on 2011-03-14
No, xrandr has nothing to do with touching the HD, out alone protected folders, so it doesn't require sudo. (Which is much appreciated - I use an xrandr script to switch my netbook to reader mode, and I have it assigned to a launcehr - I probably use it 30 times in a day, every time you'd flip an iPad upright.)

---

### Post by Krytarik on 2011-03-14
Follow this guide to include the xrandr commands into GDM's startup script:
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts]("https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts")

This way also the login screen has the desired resolution, and you may otherwise also have a re-ordering issue of the panel items.

Also, please check if indeed just the VESA driver is running, you may post the output of the command:
```
lshw -c video
```

---

### Post by shafiekd on 2011-03-15
Here's the output of the lshw -c video command:
  	 	 	 	p { margin-bottom: 0.08in; }  *-display:0              
        description: VGA compatible controller 
        product: Mobile 4 Series Chipset Integrated Graphics Controller 
        vendor: Intel Corporation 
        physical id: 2 
        bus info: pci@0000:00:02.0 
        version: 07 
        width: 64 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list rom 
        configuration: driver=i915 latency=0 
        resources: irq:28 memory:50000000-503fffff memory:40000000-4fffffff(prefetchable) ioport:5110(size=8) 
   *-display:1 UNCLAIMED 
        description: Display controller 
        product: Mobile 4 Series Chipset Integrated Graphics Controller 
        vendor: Intel Corporation 
        physical id: 2.1 
        bus info: pci@0000:00:02.1 
        version: 07 
        width: 64 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list 
        configuration: latency=0 
        resources: memory:52500000-525fffff 



I can only open /etc/gdm/Pressession/Default in read only mode, cant edit it in either gedit or vi.
Also not sure what they mean by "  For GDM, try putting them right before initctl -q emit login-session-start DISPLAY_MANAGER=gdm in /etc/gdm/Init/Default" on the Wiki.


thanks

 
 
pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in;*

---

### Post by Krytarik on 2011-03-15
1.) You are running the correct driver, fine.

2.) It actually means:
```
gksudo gedit /etc/gdm/Init/Default
```/etc/gdm/Init/Default:
```
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

#if [ -x '/usr/bin/xsplash' ];
#then
#        /usr/bin/xsplash --gdm-session --daemon
#fi

[COLOR=Red][B]xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr --output VGA1 --mode "1024x768_60.00"
[/B][/COLOR]  
/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS
  echo "$OUTPUT"
}

```

---

### Post by shafiekd on 2011-03-16
Still doesnt load at startup...
Here's what my file looks like for gksudo gedit /etc/gdm/Init/Default

#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

#if [ -x '/usr/bin/xsplash' ];
#then
#        /usr/bin/xsplash --gdm-session --daemon
#fi

xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr --output VGA1 --mode "1024x768_60.00"

/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS
  echo "$OUTPUT"
}

sysresources=/etc/X11/Xresources

# merge in defaults
if [ -f "$sysresources" ]; then
    xrdb -merge "$sysresources"
fi

sysmodmap=/etc/X11/Xmodmap

XMODMAP=`gdmwhich xmodmap`
if [ "x$XMODMAP" != "x" ] ; then
  if [ "x$GDM_PARENT_DISPLAY" = "x" ]; then
    if [ -f $sysmodmap ]; then
      $XMODMAP $sysmodmap
    fi
  else
    ( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $XMODMAP -pke ) | $XMODMAP -
  fi

  #
  # Switch Sun's Alt and Meta mod mappings
  #

  UNAME=`gdmwhich uname`
  PROCESSOR=`$UNAME -p`
  if [ "x$PROCESSOR" = "xsparc" ]; then
    if $XMODMAP | /usr/bin/grep mod4 | /usr/bin/grep Alt > /dev/null 2>/dev/null
    then
      $XMODMAP -e "clear Mod1" \
               -e "clear Mod4" \
               -e "add Mod1 = Alt_L" \
               -e "add Mod1 = Alt_R" \
               -e "add Mod4 = Meta_L" \
               -e "add Mod4 = Meta_R"
    fi
  fi
fi

SETXKBMAP=`gdmwhich setxkbmap`
if [ "x$SETXKBMAP" != "x" ] ; then
  # FIXME: is this all right?  Is this completely on crack?
  # What this does is move the xkb configuration from the GDM_PARENT_DISPLAY
  # FIXME: This should be done in code.  Or there must be an easier way ...
  if [ -n "$GDM_PARENT_DISPLAY" ]; then
    XKBSETUP=`( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $SETXKBMAP -v )`
    if [ -n "$XKBSETUP" ]; then
      XKBKEYMAP=`echo "$XKBSETUP" | grep '^keymap' | awk '{ print $2 }'`
      XKBTYPES=`echo "$XKBSETUP" | grep '^types' | awk '{ print $2 }'`
      XKBCOMPAT=`echo "$XKBSETUP" | grep '^compat' | awk '{ print $2 }'`
      XKBSYMBOLS=`echo "$XKBSETUP" | grep '^symbols' | awk '{ print $2 }'`
      XKBGEOMETRY=`echo "$XKBSETUP" | grep '^geometry' | awk '{ print $2 }'`
      if [ -n "$XKBKEYMAP" ]; then
        $SETXKBMAP -keymap "$XKBKEYMAP"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" -a -n "$XKBGEOMETRY" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS" -geometry "$XKBGEOMETRY"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS"
      elif [ -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -symbols "$XKBSYMBOLS"
      fi
    fi
  fi
fi

exit 0


Hope that helps....

Thanks

---

### Post by Krytarik on 2011-03-16
Do the xrandr commands work when run in a terminal?

If not, post the output of "xrandr" and those from the commands.

---

### Post by shafiekd on 2011-03-21
Sorry for the late reply....

Output from running the command....
shafiekd@Shafiekd-laptop:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  31
  Current serial number in output stream:  31
shafiekd@Shafiekd-laptop:~$ xrandr --addmode VGA1 1024x768_60.00
shafiekd@Shafiekd-laptop:~$ xrandr --addmode VGA1 1024x768_60.00
shafiekd@Shafiekd-laptop:~$ xrandr --output VGA1 --mode "1024x768_60.00"

It never use to give me this error before though....
"X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  31
  Current serial number in output stream:  3"

output of 'xrandr' command:
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      75.0 +   60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
   1024x768_60.00   59.4* 
LVDS1 connected 800x600+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0 +
   1360x768       59.8  
   800x600        60.3* 
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)I have switched to KDE (Kubuntu Plasma Desktop) in the meantime, and i get the 1024x768 display from boot.[B]
Would[/B]still love to get that resolution with 
gnome though...

---

### Post by Krytarik on 2011-03-21
> **shafiekd said:**
> 
It never use to give me this error before though....
```
"X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  31
  Current serial number in output stream:  3"
```You get that error because a mode with those name already exists, and it is even set:
> **shafiekd said:**
> 
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      75.0 +   60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
  **[COLOR=Blue]1024x768_60.00   59.4*[/COLOR]**[B][COLOR=Blue]
[/COLOR] [/B]LVDS1 connected 800x600+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0 +
   1360x768       59.8  
   800x600        60.3* 
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
```
But you set that mode for "VGA1", which may be an external monitor, connected via the VGA port. Instead you need to set "LVDS1" that way. And just to make sure you have the most proper modeline, use the "cvt" command to get those. Also, you don't need to run "--addmode" twice.

---

