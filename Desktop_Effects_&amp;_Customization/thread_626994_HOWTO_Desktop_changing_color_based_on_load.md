---
title: "HOWTO: Desktop changing color based on load"
date: 2007-11-29
forum: Desktop Effects &amp; Customization
---

### Post by kane77 on 2007-11-29
So I made this little script that changes the desktop color with different load averages.
So far it's pretty simple - it takes average load values from /proc/loadavg (there are 3 - average for 1 min, 5 min and 15 min) and turns them into RGB values in endless loop...

**Red** value is taken from 1min average.. so if the desktop is reddish it means that in last minute there's been high load on the computer.
**Green**value is taken from 5min average... if the desktop is green it means that in last 5 minutes the load has been high, but not in last minute...
**Blue** represents 15minute load average - if the desktop is blue the load in 15 minutes was high but not in last 5 or 1 minute...

Generaly the lighter the color is the more load is on the computer... maximum would be white then you know you've been killing your processor for at least 15 minutes :)

Here is the script:
```
#!/usr/bin/ruby

@primary = "/desktop/gnome/background/primary_color"
@secondary = "/desktop/gnome/background/secondary_color"
while ( 1 )
     @load=`cat /proc/loadavg`; 
    @r,@g,@b = @load.split(' ')
    @r=@r.to_f*@r.to_f
    @g=@g.to_f*@g.to_f
    @b=@b.to_f*@b.to_f
    # scale up to the range 0-255, but cap it at 255 
    @r = @r *50 
    if (@r > 255) then @r = 255 end
    @g = @g * 40 
    if (@g > 255) then @g = 255 end
    @b = @b * 30 
    if (@b > 255) then @b = 255 end # convert to hex 
    @load = sprintf("%02X%02X%02X",@r,@g,@b)
    @neg = sprintf("%02X%02X%02X",@r/2,@g/2,@b/2)
    
    # set the color 
    system("gconftool-2 -t str --set #{@primary} '##{@load}'")
    system("gconftool-2 -t str --set #{@secondary} '##{@neg}'")
    sleep 1 # Here you can set the update rate (the higher the number
               # the less often it updates)
end
```
**Installation and running:**
Just put this script into a .rb file, make it runnable ```
chmod +x <your_filename>.rb
``` and run it ```
./<yourfilename>.rb
```. 
Be sure to first disable wallpaper and set the **Colors** to gradient (either horizontal or vertical), you can also set it to plain color but it's not that pretty.
Bear in mind that you need ruby installed to run ruby scripts.

So far I only use the load for primary color and set the secondary color to half of the primary.. I plan to change the secondary color according to something else (such as ram/cpu percentage).

You can also help me by submitting your ideas. Or help me tuning the parameters. (I have pretty high load on my computer so it might look too dark on yours). Alternatively you can submitt your minimum maximum load values...

Somebody "speaking" Ruby should verify this script so people know it's safe...

---

### Post by kane77 on 2007-12-01
has anyone tried it?

---

### Post by kane77 on 2008-03-20
here is the program rewritten:
```
#!/usr/bin/ruby

@primary = "/desktop/gnome/background/primary_color"
@secondary = "/desktop/gnome/background/secondary_color"

def clip value;	value>255 ? 255 : value; end

while (1)
  @load=`cat /proc/loadavg`; 
  @r,@g,@b = @load.split(' ').map do |color|
  	clip(color.to_f**2 * (50-10))
	end
	@load = sprintf("%02X%02X%02X",@r,@g,@b)
  @neg = sprintf("%02X%02X%02X",@r/2,@g/2,@b/2)
  system("gconftool-2 -t str --set #{@primary} '##{@load}'")
  system("gconftool-2 -t str --set #{@secondary} '##{@neg}'")
  sleep 3
end
```

---

### Post by GTengineer on 2008-03-20
I tried it and it seems to work although there is quite a bit of a delay between actual cpu load and the display. The refresh rate is pretty slow too. The problem I see though is that I usually have so many windows opened that the desktop is never even visible and I also like my wallpaper ;)

---

### Post by durand on 2008-03-21
Whoa, pretty cool! I'm gonna see if this can be filtered through a transparent svg wallpaper.

EDIT: it works great :D and looks really sweet!

If I wanted to export @primary and @secondary to a text file so that I can use it in another script, can I add this line to the end?

```

system("echo "{@primary}" > example.tmp'")

```

I'm thinking of writing a simple script to change the colours in an svg file.

---

### Post by durand on 2008-03-21
I'm currently using the script with this svg:

[http://ubuntuforums.org/showthread.php?t=661572](http://ubuntuforums.org/showthread.php?t=661572)

it really does look awesome! I disabled the desktop temporarily to screenshot it.

---

