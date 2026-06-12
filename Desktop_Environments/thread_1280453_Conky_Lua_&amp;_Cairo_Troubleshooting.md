---
title: "Conky Lua &amp; Cairo Troubleshooting"
date: 2009-10-02
forum: Desktop Environments
---

### Post by londonali1010 on 2009-10-02
Hi guys...It seems as though there are several of you out there having trouble getting started with Conky's Cairo bindings for Lua. In case you don't know what I'm on about, Cairo bindings for Lua mean that you can draw nifty things directly to the Conky window, like this:
[ATTACH]130467[/ATTACH]
The first thing you'll need to do to get this up and running is to get a copy of Conky 1.7.2, either from [source]("http://conky.sourceforge.net"), or from a [PPA]("https://launchpad.net/~norsetto/+archive/ppa/+packages"). If you compile from source, ensure that you enable Cairo and Lua (and you may as well enable imlib2 while you're there). If you download the .deb, make sure you choose the "all" version.

I have made some scripts already that you can try out; you can download them from [Conky Hardcore]("http://conky.linux-hardcore.com/?page_id=2880").  I've also written a blog post over on the [Conky Blog]("http://blog.conky.be/?p=67") to get you started writing your own.

If you have any more trouble, please post here, with your script, and the output of
```
conky -v
```

---

### Post by mobilediesel on 2009-10-02
> **londonali1010 said:**
> Hi guys...It seems as though there are several of you out there having trouble getting started with Conky's Cairo bindings for Lua. In case you don't know what I'm on about, Cairo bindings for Lua mean that you can draw nifty things directly to the Conky window, like this:
[ATTACH]130467[/ATTACH]
The first thing you'll need to do to get this up and running is to get a copy of Conky 1.7.2, either from [source]("http://conky.sourceforge.net"), or from a [PPA]("https://launchpad.net/~norsetto/+archive/ppa/+packages"). If you compile from source, ensure that you enable Cairo and Lua (and you may as well enable imlib2 while you're there). If you download the .deb, make sure you choose the "all" version.

I have made some scripts already that you can try out; you can download them from [Conky Hardcore]("http://conky.linux-hardcore.com/?page_id=2880").  I've also written a blog post over on the [Conky Blog]("http://blog.conky.be/?p=67") to get you started writing your own.

If you have any more trouble, please post here, with your script, and the output of
```
conky -v
```

I'm going to end up upgrading from Hardy to Jaunty or Karmic just to get Conky 1.7.2! It looks like the tolua++ it what's giving me the problem. Conky wont compile without tolua++ and I can't get tolua++ installed.

The PPA linked above tells me there's a dependency that cannot be met. I imagine that's because there's no .deb for Hardy.

After seeing your rings script, my CPU, MEM and DRIVE bars are looking uglier by the day!

---

### Post by BornTwisted on 2009-10-02
Hi Ali, a couple of things have crossed my mind about the display of the rings, is there an easy way to get the rings to work anti-clockwise and is it possible to make them ovals?

---

### Post by dk75 on 2009-10-02
OK. So I'm doing "parachute drop" here.

Heres 3 helepers LUA script to make Clock ( at the moment ).
It needs to be unpacked and copied to "/usr/share/lua51" to work properly.

Then theres clock script:
```

-- Conky Lua Cairo clock
--
do
	require 'ubuntuforums-conky-main'
	require 'ubuntuforums-conky-cairo'

	function conky_draw_clock(radius,thick,alpha)
		if (radius == 0) or (thick == 0) then return end
		cr, w, h = conky_cairo_window_hook()
		if ((radius+thick)*2 > w) then radius = (w/2)-thick; end
		if ((radius+thick)*2 > h) then radius = (h/2)-thick; end
		local x, y = radius+thick, radius+thick
		cairo_set_line_width(cr, thick)
		cairo_set_source_rgba(cr, conky_cairo_rgb2rgba(0xFFFFFF,1))
		cairo_arc(cr, x, y, radius, 0/180*math.pi, 360/180*math.pi)
		cairo_stroke(cr)
		cairo_set_line_width(cr, thick/2)
		for pins = 0, 330, 30 do
			cairo_move_to(cr, conky_main_pointATcircle(x,y,pins,radius*0.95))
			cairo_line_to(cr, conky_main_pointATcircle(x,y,pins,radius*0.85))
		end
		cairo_stroke(cr)
		cairo_set_line_width(cr, thick)
		cairo_set_source_rgba(cr, conky_cairo_rgb2rgba(0xFFFFFF,0.5))
		cairo_arc(cr, x, y, thick, 0, 2*math.pi)
		cairo_stroke(cr)
		
		local h_alpha, m_alpha, s_alpha = conky_main_time2angle()
		
		cairo_set_line_width(cr, thick*1.5)
		cairo_set_source_rgba(cr, conky_cairo_rgb2rgba(0x606060,0.5))
		cairo_move_to(cr, conky_main_pointATcircle(x,y,h_alpha,thick*2))
		cairo_line_to(cr, conky_main_pointATcircle(x,y,h_alpha,radius*0.5))
		cairo_stroke(cr)
		
		cairo_set_line_width(cr, thick*0.8)
		cairo_set_source_rgba(cr, conky_cairo_rgb2rgba(0xFFFFFF,0.5))
		cairo_move_to(cr, conky_main_pointATcircle(x,y,m_alpha,thick*2.5))
		cairo_line_to(cr, conky_main_pointATcircle(x,y,m_alpha,radius*0.8))
		cairo_stroke(cr)
		
		cairo_set_line_width(cr, thick*0.2)
		cairo_set_source_rgba(cr, conky_cairo_rgb2rgba(0xff0000,1))
		cairo_move_to(cr, conky_main_pointATcircle(x,y,s_alpha,thick*4))
		cairo_line_to(cr, conky_main_pointATcircle(x,y,s_alpha,radius*0.9))
		cairo_stroke(cr)
	end
end

```


and theres corresponding conkyrc:
```

background no
use_xft yes
xftfont Bitstream Vera Sans Mono:size=13.5
xftalpha 0.8
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_colour hotpink
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 500
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 0
border_inner_margin 16
border_width 1
default_color white
default_shade_color black
default_outline_color black
alignment top_left
gap_x 100
gap_y 500
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer right
max_port_monitor_connections 80
max_specials 256
max_user_text 256
#text_buffer_size 16384
imlib_cache_size 16777216
color0 ffffff
lua_load ~/.conky/lua/analog-clock.lua
lua_draw_hook_post conky_draw_clock 200 10

TEXT














${execp ps u -p $(pidof conky) |awk '/conky/ {sub(".*-","",$NF); print $NF,"${goto 80}CPU:",$3"%","${goto 190}MEM:",$4"%"}'}

```

PS: test9 is the Conky with Cairo-Clock

---

### Post by londonali1010 on 2009-10-02
> **mobilediesel said:**
> I'm going to end up upgrading from Hardy to Jaunty or Karmic just to get Conky 1.7.2! It looks like the tolua++ it what's giving me the problem. Conky wont compile without tolua++ and I can't get tolua++ installed.

The PPA linked above tells me there's a dependency that cannot be met. I imagine that's because there's no .deb for Hardy.

After seeing your rings script, my CPU, MEM and DRIVE bars are looking uglier by the day!

How come you haven't upgraded already?! Just kidding, that's your decision!

You can probably write a script in Python to use Cairo, rather than Lua/Cairo, and then use ${exec} to run it, but it would be harder...

> **BornTwisted said:**
> Hi Ali, a couple of things have crossed my mind about the display of the rings, is there an easy way to get the rings to work anti-clockwise and is it possible to make them ovals?

Probably! :)
There's a cairo_arc_negative() function, which is the same as the cairo_arc function, just counterclockwise. I'm not sure about drawing an oval/ellipse...

---

### Post by dk75 on 2009-10-02
"cairo_curve_to" draws Bezier - it might be usable, but we need some mathematical function to compute needed Bezier subpoints to draw oval/elipse with.

---

### Post by londonali1010 on 2009-10-02
Okay, then, use this, from the Cairo documentation:

> The arc is circular in user space. To achieve an elliptical arc, you can scale the current transformation matrix by different amounts in the X and Y directions. For example, to draw an ellipse in the box given by x, y, width, height:

```
cairo_save (cr);
cairo_translate (cr, x + width / 2., y + height / 2.);
cairo_scale (cr, width / 2., height / 2.);
cairo_arc (cr, 0., 0., 1., 0., 2 * M_PI);
cairo_restore (cr);
```

---

### Post by BornTwisted on 2009-10-02
> **londonali1010 said:**
> There's a cairo_arc_negative() function, which is the same as the cairo_arc function, just counterclockwise.

Thanks Ali, not sure if i did it correctly but it's working :) And no errors showing in the terminal.

Changed cairo_arc to cairo_arc_negative in the -- Draw background ring and -- Draw indicator ring sections (working from your rings.lua script).

EDIT:
D'oh, just noticed that the background alpha doesn't show if i only edit those two parts.

---

### Post by mobilediesel on 2009-10-02
> **londonali1010 said:**
> How come you haven't upgraded already?! Just kidding, that's your decision!
Only because it's the "Long Term Support" version. I'm really re-thinking the need for that since there's newer versions of most software in the newer versions of Ubuntu.
> You can probably write a script in Python to use Cairo, rather than Lua/Cairo, and then use ${exec} to run it, but it would be harder...
I have been looking at Python tutorials already. I even found one aimed at cairo with Python. [http://www.tortall.net/mu/wiki/CairoTutorial](http://www.tortall.net/mu/wiki/CairoTutorial)

I like to think I'm good with Bash scripting but it's not great for anything beyond simple text manipulation.

---

### Post by srbharadwaj on 2009-10-03
ok i hav started playing around with lua scripts....one question from my side....how do i place the graphical object within the conky window.......in other words if i write a lua script for clock or rings wat parameter determines the position of the clock or rings within the conky window?

---

### Post by londonali1010 on 2009-10-03
> **srbharadwaj said:**
> ok i hav started playing around with lua scripts....one question from my side....how do i place the graphical object within the conky window.......in other words if i write a lua script for clock or rings wat parameter determines the position of the clock or rings within the conky window?

If you draw an arc (circle) with Cairo, you have to define xc, yc, which are the coordinates of the centre of the are. Your Conky window by default defines a coordinate space in pixels, like graph paper, where (0,0) is the top left of your Conky, and (w,h) is the bottom right, if you've defined
```
w=conky_window.width
h=conky_window.height
```
If you want to make an arc in the centre, for instance, you would use something like
```
cairo_arc(cr, w/2, h/2, w/4, 0, 2*math.pi)
```
For straight line drawing, you can use
```
cairo_move_to(cr, x, y)
cairo_line_to(cr, x, y)
cairo_arc_to(cr, x, y)
```
where x and y are always in pixels as defined by the coordinate space.

Hope this helps!

---

### Post by searchOne on 2009-10-04
Hello londonali1010,

i have a Problem with your new Skript "rings.lua".
I have copied the script from here
[http://conky.linux-hardcore.com/?page_id=2800](http://conky.linux-hardcore.com/?page_id=2800)

The rings are not indicated and this message comes in the terminal:

```

search@Genius:~$ conky -c /home/search/.conkyrc
Conky: llua_load: /home/search/conky/lua/rings.lua:87: '}' expected (to close '{' at line 83) near 'bg_colour'
Conky: desktop window (13f) is root window
Conky: window type - normal
Conky: drawing to created window (0x2400001)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_ring_stats execution failed: attempt to call a nil value

```:confused:

This is the Skript:
```

--[[
Ring Meters by londonali1010 (2009)

This script draws percentage meters as rings. It is fully customisable; all options are described in the script.

IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.

To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/rings.lua
    lua_draw_hook_pre ring_stats
    
Changelog:
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]

settings_table = {
    {
        -- Edit this table to customise your rings.
        -- You can create more rings simply by adding more elements to settings_table.
        -- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
        name='cpu',
        -- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
        arg='cpu0',
        -- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
        max=100,
        -- "bg_colour" is the colour of the base ring.
        bg_colour=0xCDCDC1,
        -- "bg_alpha" is the alpha value of the base ring.
        bg_alpha=0.5,
        -- "fg_colour" is the colour of the indicator part of the ring.
        fg_colour=0xFF0000,
        -- "fg_alpha" is the alpha value of the indicator part of the ring.
        fg_alpha=0.8,
        -- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
        x=120, y=120,
        -- "radius" is the radius of the ring.
        radius=81,
        -- "thickness" is the thickness of the ring, centred around the radius.
        thickness=10,
        -- "angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
        angle=90
    },
    {
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=0xCDCDC1,
        bg_alpha=0.5,
        fg_colour=0xFF0000,
        fg_alpha=0.5,
        x=120, y=120,
        radius=93,
        thickness=10,
        angle=90
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0x1E90FF,
        fg_alpha=0.5,
        x=120, y=120,
        radius=102.5,
        thickness=5,
        angle=90
    },
    {
        name='fs_used_perc',
        arg='/',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0x00FF00,
        fg_alpha=0.5,
        x=120, y=120,
        radius=58,
        thickness=10,
        angle=90
    },
    {
        name='battery_percent',
        arg='BAT0',
        max=100
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFFFF00,
        fg_alpha=1,
        x=120, y=120,
        radius=70,
        thickness=10,
        angle=90
    },
}

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(t, pt)
    if conky_window==nil then return end
    local w,h=conky_window.width,conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual,w,h)
    
    cr=cairo_create(cs)
    
    local xc,yc,ring_r,ring_w,angle=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

    local angle_0=angle*(2*math.pi/360)-math.pi/2
    local t_arc=t*2*math.pi

    -- Draw background ring

    cairo_arc(cr,xc,yc,ring_r,0,2*math.pi)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
    
    -- Draw indicator ring

    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
    
    cairo_destroy(cr)
    cr = nil
end

function conky_cairo_cleanup()
    cairo_surface_destroy(cs)
    cs = nil
end

function conky_ring_stats()
    local function setup_rings(pt)
        local str=''
        local value=0
        
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
        
        value=tonumber(str)
        pct=value/pt['max']
        
        draw_ring(pct,pt)
    end
    
    -- Check that Conky has been running for at least 5s
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(settings_table[i])
        end
    end
end

```

line 87:
```

bg_colour=0xffffff,

```

---

### Post by searchOne on 2009-10-04
Stop, I have found the error. I have forgotten only in the line about it the comma>, ... ****!

---

### Post by londonali1010 on 2009-10-04
Found it!

In your 'battery_percent' section, you left off the comma after max=100.

Should be
```
max=100**[COLOR="Red"],[/COLOR]**
```

---

### Post by searchOne on 2009-10-04
> **londonali1010 said:**
> Found it!

In your 'battery_percent' section, you left off the comma after max=100.

Should be
```
max=100**[COLOR=Red],[/COLOR]**
```

Thanks londonali1010! :KS

---

### Post by dk75 on 2009-10-04
Anyone here knows whats exactly doing "lua_startup_hook" in developement Conky 1.7.3?
I've tryed it to draw clock background only once at Conky startup but it's not working as expected.
Seems to me, that Cairo drawings is cleared every time Conky is refreshed (since every time it needs to be done "cairo_create(cairo_create_surface())" ).

---

### Post by searchOne on 2009-10-05
Hello londonali1010,
is there with yours ring.lua script also the possibility quite easy circles to sign, without function? :confused:

Greeting
Stefan

P.S.: I find your engagement for Conky/lua-Cairo class! What you till present already everything in Really scripts produced has is the hit! Thank you. :KS :KS :KS :KS

---

### Post by dmillerct on 2009-10-08
After updating to the 1.2v of rings I am getting the following error:

```
Conky: llua_do_call: function conky_ring_stats execution failed: /home/dmiller/Conky/Scripts/rings.lua:114: attempt to perform arithmetic on local 'sa' (a nil value)

```

here is the settings_table I am using in the rings.lua file:

```
settings_table = {
	{
		-- Edit this table to customise your rings.
		-- You can create more rings simply by adding more elements to settings_table.
		-- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
		name='cpu',
		-- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
		arg='cpu0',
		-- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
		max=100,
		-- "bg_colour" is the colour of the base ring.
		bg_colour=0xffffff,
		-- "bg_alpha" is the alpha value of the base ring.
		bg_alpha=0,
		-- "fg_colour" is the colour of the indicator part of the ring.
		fg_colour=0xffffff,
		-- "fg_alpha" is the alpha value of the indicator part of the ring.
		fg_alpha=0.8,
		-- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
		x=120, y=120,
		-- "radius" is the radius of the ring.
		radius=87.5,
		-- "thickness" is the thickness of the ring, centred around the radius.
		thickness=15
	},
	{
		name='memperc',
		arg='',
		max=100,
		bg_colour=0xffffff,
		bg_alpha=0.1,
		fg_colour=0xffffff,
		fg_alpha=0.5,
		x=120, y=120,
		radius=102.5,
		thickness=5,
		start_angle=0,
		end_angle=360
	},
	{
		name='fs_used_perc',
		arg='/',
		max=100,
		bg_colour=0xffffff,
		bg_alpha=0,
		fg_colour=0xffffff,
		fg_alpha=0.5,
		x=120, y=120,
		radius=50,
		thickness=20,
		start_angle=0,
		end_angle=360
	},
	{
		name='battery_percent',
		arg='',
		max=100,
		bg_colour=0xffffff,
		bg_alpha=0.2,
		fg_colour=0xffffff,
		fg_alpha=1,
		x=120, y=120,
		radius=70,
		thickness=10,
		start_angle=0,
		end_angle=360
	},
	{
		name='wireless_link_qual',
		arg='wlan0',
		max=100,
		bg_colour=0xffffff,
		bg_alpha=0.2,
		fg_colour=0xffffff,
		fg_alpha=1,
		x=885, y=460,
		radius=82.0,
		thickness=8,
		start_angle=0,
		end_angle=360
	},

}

```

Here is line 114 in the config:

```
local angle_0=sa*(2*math.pi/360)-math.pi/2
```

It has something to do with the angles, just not sure what.

---

### Post by 5BallJuggler on 2009-10-08
@Londonali

I've been inspired by your ring threads, to the point that i'm trying something a bit different,
i've started working on a script that will allow for a moving start and finish angle.
This is as far as i have got, some help would be appreciated.



Thanks
Phil
```

function draw_ring(cr,t,pt)
	local w,h=conky_window.width,conky_window.height
	local secs=os.date("%S")
	local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
	
	local angle_a=sa*(2*math.pi/360)-math.pi/2
	local angle_0=-1.570796+((secs*6)*0.017453)-0.03
	local angle_f=angle_0+0.3
	local angle_b=ea*(2*math.pi/360)-math.pi/2
	local t_arc=t*(angle_f-angle_0)

	-- Draw background ring

	cairo_arc(cr,xc,yc,ring_r,angle_a,angle_b)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
	
	-- Draw indicator ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
end

```

What I'm trying to do is have a script that will only show the current second/minute/hour/day/date/year....etc in a ring, i've add a series of screenshots of what the above code is doing at the moment to hopefully explain better.

i'm also trying to make the background ring appear to rotate also. but that's not in the screenies.

the bit that i'm interested in is at the bottom of the screen, just to the right of the upspeed eth0 graph.

Also, I'd like to work together on this, I'm not hoping you will do all the work ;-)

---

### Post by londonali1010 on 2009-10-08
> **5BallJuggler said:**
> @Londonali

I've been inspired by your ring threads, to the point that i'm trying something a bit different,
i've started working on a script that will allow for a moving start and finish angle.
This is as far as i have got, some help would be appreciated.



Thanks
Phil
```

function draw_ring(cr,t,pt)
	local w,h=conky_window.width,conky_window.height
	local secs=os.date("%S")
	local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
	
	local angle_a=sa*(2*math.pi/360)-math.pi/2
	local angle_0=-1.570796+((secs*6)*0.017453)-0.03
	local angle_f=angle_0+0.3
	local angle_b=ea*(2*math.pi/360)-math.pi/2
	local t_arc=t*(angle_f-angle_0)

	-- Draw background ring

	cairo_arc(cr,xc,yc,ring_r,angle_a,angle_b)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
	
	-- Draw indicator ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
end

```

What I'm trying to do is have a script that will only show the current second/minute/hour/day/date/year....etc in a ring, i've add a series of screenshots of what the above code is doing at the moment to hopefully explain better.

i'm also trying to make the background ring appear to rotate also. but that's not in the screenies.

the bit that i'm interested in is at the bottom of the screen, just to the right of the upspeed eth0 graph.

Also, I'd like to work together on this, I'm not hoping you will do all the work ;-)

Oh, okay, I see! If it were me, I would set the length of the moving bit, then draw your arc centred on the secs (or whatever) value...so try:
```
local arc_w = 2*math.pi/60 -- Sets width of arc to 1/60th of a circle
local angle_0 = sa*(2*math.pi/360)-math.pi/2 -- Converts the starting angle to radians & translates to starting from the top
local t_arc = angle_0 + t*2*math.pi -- Converts the percentage to a part of 2*pi radians & adds the starting angle
```
Then to draw the indicator ring:
```
cairo_arc(cr, xc, yc, ring_r, t_arc-arc_w, t_arc+arc_w)
```
I haven't tried it myself, but have a go!

I don't get what you mean by moving the background ring around...Can you elaborate?

---

### Post by 5BallJuggler on 2009-10-08
> **londonali1010 said:**
> Oh, okay, I see! If it were me, I would set the length of the moving bit, then draw your arc centred on the secs (or whatever) value...so try:
```
local arc_w = 2*math.pi/60 -- Sets width of arc to 1/60th of a circle
local angle_0 = sa*(2*math.pi/360)-math.pi/2 -- Converts the starting angle to radians & translates to starting from the top
local t_arc = angle_0 + t*2*math.pi -- Converts the percentage to a part of 2*pi radians & adds the starting angle
```
Then to draw the indicator ring:
```
cairo_arc(cr, xc, yc, ring_r, t_arc-arc_w, t_arc+arc_w)
```
I haven't tried it myself, but have a go!

I don't get what you mean by moving the background ring around...Can you elaborate?

Fantastic, works a treat, I added the original "angle_f" line

```
function draw_ring(cr,t,pt)
	local w,h=conky_window.width,conky_window.height
	local port=pt['max']
	local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
	
	local arc_w = 2*math.pi/port -- Sets width of arc to 1/"max"nth of a circle
	local angle_0 = sa*(2*math.pi/360)-math.pi/2 -- Converts the starting angle to radians & translates to starting from the top
	local angle_f = ea*(2*math.pi/360)-math.pi/2
	local t_arc = angle_0 + t*2*math.pi -- Converts the percentage to a part of 2*pi radians & adds the starting angle

	-- Draw background ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
	
	-- Draw indicator ring

	cairo_arc(cr, xc, yc, ring_r, t_arc-arc_w, t_arc+arc_w)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
end

```

I've also coded for the 'max' value to give different size arcs of movement, 
What do you think??

Phil

ps Thanks very much.
pps I'll post on the Conky thread tomorrow.

---

### Post by londonali1010 on 2009-10-08
> **5BallJuggler said:**
> Fantastic, works a treat, I added the original "angle_f" line

```
function draw_ring(cr,t,pt)
	local w,h=conky_window.width,conky_window.height
	local port=pt['max']
	local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
	
	local arc_w = 2*math.pi/port -- Sets width of arc to 1/"max"nth of a circle
	local angle_0 = sa*(2*math.pi/360)-math.pi/2 -- Converts the starting angle to radians & translates to starting from the top
	local angle_f = ea*(2*math.pi/360)-math.pi/2
	local t_arc = angle_0 + t*2*math.pi -- Converts the percentage to a part of 2*pi radians & adds the starting angle

	-- Draw background ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
	
	-- Draw indicator ring

	cairo_arc(cr, xc, yc, ring_r, t_arc-arc_w, t_arc+arc_w)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
end

```

I've also coded for the 'max' value to give different size arcs of movement, 
What do you think??

Phil

ps Thanks very much.
pps I'll post on the Conky thread tomorrow.

Yeah, that's good, so your hour will be 1/12th of the circle, minute & seconds will be 1/60th, and normal percentages will be 1/100th, I guess?  You could also add another field to the settings_table, although it's starting to get ridiculous now :)

---

### Post by dmillerct on 2009-10-08
@my post,

NVM, I found it. DERP.

---

### Post by d_eckert on 2009-10-09
Hi, I am having no luck trying to get rings working.

I downloaded the rings-v1.2.lua script from conky hardcore and I copied the text for the .conkyrc from there as well, however when I run conky I get the following message:
Conky: llua_do_call: function conky_ring_stats execution failed: attempt to call a nil value

I tried deleting the battery entry from the settings_table as I am not using a laptop but that had no affect.

---

### Post by londonali1010 on 2009-10-09
> **d_eckert said:**
> Hi, I am having no luck trying to get rings working.

I downloaded the rings-v1.2.lua script from conky hardcore and I copied the text for the .conkyrc from there as well, however when I run conky I get the following message:
Conky: llua_do_call: function conky_ring_stats execution failed: attempt to call a nil value

I tried deleting the battery entry from the settings_table as I am not using a laptop but that had no affect.

Please post the output from ```
conky -v
```

Most of the people who have had this issue with my scripts have either not had Conky 1.7.2 installed, or if they did, then Cairo was not enabled.

If that's the case, you can get the official .deb for 1.7.2 here: [https://launchpad.net/~norsetto/+archive/ppa/+packages](https://launchpad.net/~norsetto/+archive/ppa/+packages)

Please note you will need at least Ubuntu 9.04.

---

### Post by dmillerct on 2009-10-09
Has anyone been able to get upspeed or downspeed variables to work with the new max setting in v1.2?

After my attempt I keep getting the following:

```
Conky: llua_do_call: function conky_ring_stats execution failed: /home/dmiller/Conky/Scripts/rings.lua:157: attempt to perform arithmetic on local 'value' (a nil value)
```

---

### Post by d_eckert on 2009-10-09
> **londonali1010 said:**
> Please post the output from ```
conky -v
```

Most of the people who have had this issue with my scripts have either not had Conky 1.7.2 installed, or if they did, then Cairo was not enabled.

If that's the case, you can get the official .deb for 1.7.2 here: [https://launchpad.net/~norsetto/+archive/ppa/+packages](https://launchpad.net/~norsetto/+archive/ppa/+packages)

Please note you will need at least Ubuntu 9.04.

Conky 1.7.2 compiled Sun Oct  4 23:14:50 UTC 2009 for Linux 2.6.24-23-server (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

---

### Post by dmillerct on 2009-10-09
OK, again, never mind. :)

I fixed it myself: [http://ubuntuforums.org/showpost.php?p=8077786&postcount=9706]("http://ubuntuforums.org/showpost.php?p=8077786&postcount=9706")

---

### Post by aymaraceci on 2009-10-11
Hi!!! 

I had a clock_ring setup working fine. But after shut down my pc, and turning on again, clock hands disapear!! (rings displays corectly). 

on my terminal it claims: 
```

Conky: llua_do_call: function conky_clock_rings execution failed: /home/aymara/clock.lua:228: attempt to perform arithmetic on local 'value' (a nil value)
```

This is the .lua table

```
--[[
Clock Rings by londonali1010 (2009)

This script draws percentage meters as rings, and also draws clock hands if you want! It is fully customisable; all options are described in the script. This script is based off a combination of my clock.lua script and my rings.lua script.

IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.

To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
	lua_load ~/scripts/clock_rings.lua
	lua_draw_hook_pre clock_rings
	
Changelog:
+ v1.0 -- Original release (30.09.2009)
]]

settings_table = {
	{
		name='cpu',
		arg='cpu0',
		max=100,
		bg_colour=0x303030,
		bg_alpha=0,
		fg_colour=0x303030,
		fg_alpha=0.8,
		x=195, y=195,
		radius=137.5,
		thickness=15,
		start_angle=0,
		end_angle=360
	},
	{
		name='memperc',
		arg='',
		max=100,
		bg_colour=0x303030,
		bg_alpha=0.1,
		fg_colour=0x303030,
		fg_alpha=0.5,
		x=195, y=195,
		radius=157,
		thickness=13,
		start_angle=0,
		end_angle=360
	},
	{
		name='fs_used_perc',
		arg='/',
		max=100,
		bg_colour=0x303030,
		bg_alpha=0,
		fg_colour=0x303030,
		fg_alpha=0.5,
		x=195, y=195,
		radius=100,
		thickness=20,
		start_angle=0,
		end_angle=360
	},
	{
		name='battery_percent',
		arg='BAT0',
		max=100,
		bg_colour=0x246D58,
		bg_alpha=0.4,
		fg_colour=0x246D58,
		fg_alpha=1,
		x=195, y=195,
		radius=120,
		thickness=10,
		start_angle=0,
		end_angle=360
	},
	{
		name='wireless_link_qual_perc',
		arg='wlan0',
		max=100,
		bg_colour=0x303030,
		bg_alpha=0.1,
		fg_colour=0x303030,
		fg_alpha=0.9,
		x=195, y=195,
		radius=80,
		thickness=12.5,
		start_angle=0,
		end_angle=360
	},
	{
		name='time',
		arg='%I',
		max=12,
		bg_colour=0x303030,
		bg_alpha=0.1,
		fg_colour=0x303030,
		fg_alpha=0.9,
		x=195, y=195,
		radius=28,
		thickness=3.5,
		start_angle=0,
    		end_angle=360
	},
	{
		name='time',
		arg='%M',
		max=60,
		bg_colour=0xFFFFFF,
		bg_alpha=0.1,
		fg_colour=0xFFFFFF,
		fg_alpha=0.95,
		x=195, y=195,
		radius=33,
		thickness=3.5,
		start_angle=0,
    		end_angle=360
	},
	{
		name='time',
		arg='%S',
		max=60,
		bg_colour=0x246D58,
		bg_alpha=0.1,
		fg_colour=0x246D58,
		fg_alpha=1.0,
		x=195, y=195,
		radius=13.5,
		thickness=23,
		start_angle=0,
		end_angle=360
	},
}

-- Use these settings to define the origin and extent of your clock.

clock_r=125

-- "clock_x" and "clock_y" are the coordinates of the centre of the clock, in pixels, from the top left of the Conky window.

clock_x=195	
clock_y=195

show_seconds=true

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(cr,t,pt)
	local w,h=conky_window.width,conky_window.height
	
	local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

	local angle_0=sa*(2*math.pi/360)-math.pi/2
	local angle_f=ea*(2*math.pi/360)-math.pi/2
	local t_arc=t*(angle_f-angle_0)

	-- Draw background ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
	
	-- Draw indicator ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
end

function draw_clock_hands(cr,xc,yc)
	local secs,mins,hours,secs_arc,mins_arc,hours_arc
	local xh,yh,xm,ym,xs,ys
	
	secs=os.date("%S")	
	mins=os.date("%M")
	hours=os.date("%I")
		
	secs_arc=(2*math.pi/60)*secs
	mins_arc=(2*math.pi/60)*mins+secs_arc/60
	hours_arc=(2*math.pi/12)*hours+mins_arc/12
		
	-- Draw hour hand
	
	xh=xc+0.7*clock_r*math.sin(hours_arc)
	yh=yc-0.7*clock_r*math.cos(hours_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xh,yh)
	
	cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
	cairo_set_line_width(cr,5)
	cairo_set_source_rgba(cr,1,1,1,0.8)
	cairo_stroke(cr)
	
	-- Draw minute hand
	
	xm=xc+clock_r*math.sin(mins_arc)
	ym=yc-clock_r*math.cos(mins_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xm,ym)
	
	cairo_set_line_width(cr,3)
	cairo_stroke(cr)
	
	-- Draw seconds hand
	
	if show_seconds then
		xs=xc+clock_r*math.sin(secs_arc)
		ys=yc-clock_r*math.cos(secs_arc)
		cairo_move_to(cr,xc,yc)
		cairo_line_to(cr,xs,ys)
	
		cairo_set_line_width(cr,1)
		cairo_stroke(cr)
	end
end

function conky_clock_rings()
	local function setup_rings(cr,pt)
		local str=''
		local value=0

		str=string.format('${%s %s}',pt['name'],pt['arg'])
		str=conky_parse(str)

		value=tonumber(str)
		pct=value/pt['max']

		draw_ring(cr,pct,pt)
	end

	
	-- Check that Conky has been running for at least 5s

	if conky_window==nil then return end
	local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
	
	local cr=cairo_create(cs)	
	
	local updates=conky_parse('${updates}')
	update_num=tonumber(updates)
	
	if update_num>5 then
		for i in pairs(settings_table) do
			setup_rings(cr,settings_table[i])
		end
	end
	
	draw_clock_hands(cr,clock_x,clock_y)
end 
```

I've already tryed kill conky and start it again, also change the compiz manager to metacity and backwards... no changes...

---

### Post by dk75 on 2009-10-11
> **aymaraceci said:**
> Hi!!! 

I had a clock_ring setup working fine. But after shut down my pc, and turning on again, clock hands disapear!! (rings displays corectly). 

on my terminal it claims: 
```

Conky: llua_do_call: function conky_clock_rings execution failed: /home/aymara/clock.lua:228: attempt to perform arithmetic on local 'value' (a nil value)
```

This is the .lua table

```
--[[
Clock Rings by londonali1010 (2009)

This script draws percentage meters as rings, and also draws clock hands if you want! It is fully customisable; all options are described in the script. This script is based off a combination of my clock.lua script and my rings.lua script.

IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.

To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
	lua_load ~/scripts/clock_rings.lua
	lua_draw_hook_pre clock_rings
	
Changelog:
+ v1.0 -- Original release (30.09.2009)
]]

settings_table = {
	{
		name='cpu',
		arg='cpu0',
		max=100,
		bg_colour=0x303030,
		bg_alpha=0,
		fg_colour=0x303030,
		fg_alpha=0.8,
		x=195, y=195,
		radius=137.5,
		thickness=15,
		start_angle=0,
		end_angle=360
	},
	{
		name='memperc',
		arg='',
		max=100,
		bg_colour=0x303030,
		bg_alpha=0.1,
		fg_colour=0x303030,
		fg_alpha=0.5,
		x=195, y=195,
		radius=157,
		thickness=13,
		start_angle=0,
		end_angle=360
	},
	{
		name='fs_used_perc',
		arg='/',
		max=100,
		bg_colour=0x303030,
		bg_alpha=0,
		fg_colour=0x303030,
		fg_alpha=0.5,
		x=195, y=195,
		radius=100,
		thickness=20,
		start_angle=0,
		end_angle=360
	},
	{
		name='battery_percent',
		arg='BAT0',
		max=100,
		bg_colour=0x246D58,
		bg_alpha=0.4,
		fg_colour=0x246D58,
		fg_alpha=1,
		x=195, y=195,
		radius=120,
		thickness=10,
		start_angle=0,
		end_angle=360
	},
	{
		name='wireless_link_qual_perc',
		arg='wlan0',
		max=100,
		bg_colour=0x303030,
		bg_alpha=0.1,
		fg_colour=0x303030,
		fg_alpha=0.9,
		x=195, y=195,
		radius=80,
		thickness=12.5,
		start_angle=0,
		end_angle=360
	},
	{
		name='time',
		arg='%I',
		max=12,
		bg_colour=0x303030,
		bg_alpha=0.1,
		fg_colour=0x303030,
		fg_alpha=0.9,
		x=195, y=195,
		radius=28,
		thickness=3.5,
		start_angle=0,
    		end_angle=360
	},
	{
		name='time',
		arg='%M',
		max=60,
		bg_colour=0xFFFFFF,
		bg_alpha=0.1,
		fg_colour=0xFFFFFF,
		fg_alpha=0.95,
		x=195, y=195,
		radius=33,
		thickness=3.5,
		start_angle=0,
    		end_angle=360
	},
	{
		name='time',
		arg='%S',
		max=60,
		bg_colour=0x246D58,
		bg_alpha=0.1,
		fg_colour=0x246D58,
		fg_alpha=1.0,
		x=195, y=195,
		radius=13.5,
		thickness=23,
		start_angle=0,
		end_angle=360
	},
}

-- Use these settings to define the origin and extent of your clock.

clock_r=125

-- "clock_x" and "clock_y" are the coordinates of the centre of the clock, in pixels, from the top left of the Conky window.

clock_x=195	
clock_y=195

show_seconds=true

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(cr,t,pt)
	local w,h=conky_window.width,conky_window.height
	
	local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

	local angle_0=sa*(2*math.pi/360)-math.pi/2
	local angle_f=ea*(2*math.pi/360)-math.pi/2
	local t_arc=t*(angle_f-angle_0)

	-- Draw background ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
	
	-- Draw indicator ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
end

function draw_clock_hands(cr,xc,yc)
	local secs,mins,hours,secs_arc,mins_arc,hours_arc
	local xh,yh,xm,ym,xs,ys
	
	secs=os.date("%S")	
	mins=os.date("%M")
	hours=os.date("%I")
		
	secs_arc=(2*math.pi/60)*secs
	mins_arc=(2*math.pi/60)*mins+secs_arc/60
	hours_arc=(2*math.pi/12)*hours+mins_arc/12
		
	-- Draw hour hand
	
	xh=xc+0.7*clock_r*math.sin(hours_arc)
	yh=yc-0.7*clock_r*math.cos(hours_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xh,yh)
	
	cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
	cairo_set_line_width(cr,5)
	cairo_set_source_rgba(cr,1,1,1,0.8)
	cairo_stroke(cr)
	
	-- Draw minute hand
	
	xm=xc+clock_r*math.sin(mins_arc)
	ym=yc-clock_r*math.cos(mins_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xm,ym)
	
	cairo_set_line_width(cr,3)
	cairo_stroke(cr)
	
	-- Draw seconds hand
	
	if show_seconds then
		xs=xc+clock_r*math.sin(secs_arc)
		ys=yc-clock_r*math.cos(secs_arc)
		cairo_move_to(cr,xc,yc)
		cairo_line_to(cr,xs,ys)
	
		cairo_set_line_width(cr,1)
		cairo_stroke(cr)
	end
end

function conky_clock_rings()
	local function setup_rings(cr,pt)
		local str=''
		local value=0

		str=string.format('${%s %s}',pt['name'],pt['arg'])
		str=conky_parse(str)

		value=tonumber(str)
		pct=value/pt['max']

		draw_ring(cr,pct,pt)
	end

	
	-- Check that Conky has been running for at least 5s

	if conky_window==nil then return end
	local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
	
	local cr=cairo_create(cs)	
	
	local updates=conky_parse('${updates}')
	update_num=tonumber(updates)
	
	if update_num>5 then
		for i in pairs(settings_table) do
			setup_rings(cr,settings_table[i])
		end
	end
	
	draw_clock_hands(cr,clock_x,clock_y)
end 
```

I've already tryed kill conky and start it again, also change the compiz manager to metacity and backwards... no changes...

Change
```

		value=tonumber(str)
		pct=value/pt['max']

```
to
```

		value=tonumber(str)
		if ( value == nil ) then value = 0 end
		pct=value/pt['max']

```

---

### Post by aymaraceci on 2009-10-11
> **dk75 said:**
> Change
```

		value=tonumber(str)
		pct=value/pt['max']

```
to
```

		value=tonumber(str)
		if ( value == nil ) then value = 0 end
		pct=value/pt['max']

```

That worked!!!

THANKS!!! 

thank you for your fast and accurate answer!!!

See you arround!

---

### Post by dk75 on 2009-10-11
I've got this "value is nil" errors to but it didn't make me any trouble thought. It was always once durring start for legitimate value of "conky_window.width" and it popped up in terminal so I've ruled it out by this code.
So I've had solution at hands.

---

### Post by 5BallJuggler on 2009-10-12
Just upgraded to Karmic, and I'm getting this error.....
.....sometimes

```
Conky: X Error: type 0 Display 8dcb7e0 XID 23076034 serial 103 error_code 3 request_code 20 minor_code 0 other Display: 8dcb7e0

```

i've posted on the bug website

any ideas?

---

### Post by d_eckert on 2009-10-12
> **d_eckert said:**
> Hi, I am having no luck trying to get rings working.

I downloaded the rings-v1.2.lua script from conky hardcore and I copied the text for the .conkyrc from there as well, however when I run conky I get the following message:
Conky: llua_do_call: function conky_ring_stats execution failed: attempt to call a nil value

I tried deleting the battery entry from the settings_table as I am not using a laptop but that had no affect.

I got it working, I had saved the rings-v1.2.lua script to a different folder than ~/scripts and didn't change the lua_load line in .conkyrc to reflect this.  ](*,)](*,)](*,)

---

### Post by 5BallJuggler on 2009-10-12
](*,)

are you having troubles with the nil value still?
if so see post 31 in this thread.

---

### Post by d_eckert on 2009-10-13
nope no nil value errors anymore

---

### Post by maulbox on 2009-10-15
> **searchOne said:**
> Hello londonali1010,


Hello searchOne,
i'm interesting with conky design that you post in [here]("http://conky.linux-hardcore.com/?page_id=2962")

i'ts using londonali1010 ring script.

i'm total newbie about conky script so i try configure that script to fit in my 1024x768 screen.

but i can't find the part of cpu 2 ring, that ican't move with the other

and the calendar day colom not in line with the date (as attached)

here the script :
```

background no
use_xft yes
xftfont terminus:size=8
xftalpha 0.2
update_interval 1
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_class conky
double_buffer yes
no_buffers yes
cpu_avg_samples 2
net_avg_samples 2
use_spacer none
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
alignment tl
uppercase no
text_buffer_size 2048
imlib_cache_size 0
minimum_size 1000 290
gap_y 10
 
# &#8212; Lua Load &#8212; #
lua_load ~/scripts/rings.lua
lua_draw_hook_pre ring_stats
 
TEXT
${voffset 30}${goto 300}${diskiograph 80,300 FFFF00 FF0000 -t}${voffset -110}
${voffset 98}${goto 151}${color 1E90FF}${cpubar cpu5 2,727}${color}
${voffset -30}${goto 190}${font Zekton:size=12}CrunchBang \#! 9.04.01${font Zekton:size=8}${voffset 2}
${voffset 10}${goto 190}Conky ${conky_version}   ${goto 350}Kernel: ${kernel} 
${goto 190}${exec whoami} @ $nodename $machine   ${goto 350}Uptime: ${uptime}
${goto 190}Desktop: ${desktop_number} - ${desktop}${goto 350}CPU Temp: ${acpitemp}${offset -2} °C
${goto 190}HDD Temp: ${hddtemp /dev/sda}${offset -2} °C ${goto 350}Grafik Temp: ${nvidia temp}${offset -2} °C${if_existing /proc/net/route wlan0}${goto 450}WLAN: ${addrs wlan0}${endif}${if_existing /proc/net/route eth0}${goto 450}LAN: ${addrs eth0}${endif}
 
${goto 190}${font Zekton:Bold:size=10}Name top${goto 280}time${goto 330}cpu${goto 370}mem${goto 430}${font Zekton:Bold:size=10}Name top-io${goto 530}time${goto 580}mem${font Zekton:size=8}
${color red}${goto 190}${top name 1}   ${goto 280}${top time 1}${goto 330}${top cpu 1}${goto 370}${top mem 1} ${goto 430}${top_io 1}${top_io name 1}${goto 530}${top_io time 1}${goto 580}${top_io mem 1} ${color}${goto 690}${execi 99999 cat /proc/cpuinfo | grep "model name" -m1 | cut -d":" -f2 | cut -d" " -f2-}
${goto 190}${top name 2}   ${goto 280}${top time 2}${goto 330}${top cpu 2}${goto 370}${top mem 2}${color} ${top_io 2} ${goto 430}${top_io name 2}${goto 530}${top_io time 2}${goto 580}${top_io mem 2} ${goto 600}${execpi 3600 /home/search/conkynv.sh}
${goto 190}${top name 3}   ${goto 280}${top time 3}${goto 330}${top cpu 3}${goto 370}${top mem 3}${color} ${top_io 3} ${goto 430}${top_io name 3}${goto 530}${top_io time 3}${goto 580}${top_io mem 3}
${if_existing /proc/net/route wlan0}${voffset -210}${goto 600}${font DTPDingbats:size=18}${color green}C${font Zekton:size=12}${downspeed wlan0}${color}
 
${voffset -15}${goto 810}${font DTPDingbats:size=18}${color red}D${font Zekton:size=12}${upspeed wlan0}${color}${endif}
${if_existing /proc/net/route eth0}${voffset -210}${goto 810}${font DTPDingbats:size=18}${color green}C${font Zekton:size=12}${downspeed wlan0}${color}
 
${voffset -15}${goto 810}${font DTPDingbats:size=18}${color red}D${font Zekton:size=12}${upspeed wlan0}${color}${endif}
${font}
${voffset -215}
${goto 71}${color 1E90FF}RAM: ${memperc}%
${goto 71}${color FF0000}CPU-1: ${cpu cpu0}%
${goto 71}${color FF0000}CPU-2: ${cpu cpu1}%
${goto 71}${color FFFF00}BAT: ${battery_percent BAT0}%
${goto 71}${color 00FF00}Disk: ${fs_used_perc /}%${color}
${voffset -45}${goto 894}${font Zekton:size=10}${time %H:%M:%S}
 
${voffset -72}${color CDCD00}${goto 690}${font Zekton:Bold:size=8}${time %A}
${goto 690}${font Zekton:size=10}${time %_d %B %Y}${color}
${font LiberationMono:Bold:size=9}
${voffset -10}${execpi 60 DJS=`date +%_d`; cal -m | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${goto 690} /' | sed /" $DJS "/s/" $DJS "/" "'${color orange}'"$DJS"'${color}'" "/}
${voffset -400}
```rings.lua
```

--[[
Ring Meters by londonali1010 (2009)
 
This script draws percentage meters as rings. It is fully customisable; all options are described in the script.
 
IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.
 
To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/rings.lua
    lua_draw_hook_pre ring_stats
 
Changelog:
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]
 
settings_table = {
    {
        -- Edit this table to customise your rings.
        -- You can create more rings simply by adding more elements to settings_table.
        -- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
        name='cpu',
        -- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
        arg='cpu0',
        -- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
        max=100,
        -- "bg_colour" is the colour of the base ring.
        bg_colour=0xCDCDC1,
        -- "bg_alpha" is the alpha value of the base ring.
        bg_alpha=0.5,
        -- "fg_colour" is the colour of the indicator part of the ring.
        fg_colour=0xFF0000,
        -- "fg_alpha" is the alpha value of the indicator part of the ring.
        fg_alpha=0.8,
        -- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
        x=120, y=120,
        -- "radius" is the radius of the ring.
        radius=81,
        -- "thickness" is the thickness of the ring, centred around the radius.
        thickness=10,
        -- "angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
        angle=90
    },
    {
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=0xCDCDC1,
        bg_alpha=0.5,
        fg_colour=0xFF0000,
        fg_alpha=0.5,
        x=100, y=120,
        radius=75,
        thickness=8,
        angle=90
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0x1E90FF,
        fg_alpha=0.5,
        x=100, y=120,
        radius=82,
        thickness=5,
        angle=90
    },
    {
        name='fs_used_perc',
        arg='/',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0x00FF00,
        fg_alpha=0.5,
        x=100, y=120,
        radius=55,
        thickness=8,
        angle=90
    },
    {
        name='battery_percent',
        arg='BAT0',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFFFF00,
        fg_alpha=1,
        x=100, y=120,
        radius=65,
        thickness=8,
        angle=90
    },
    {
        name='time',
        arg='+%S',
        max=60,
        bg_colour=0xE3E3E3,
        bg_alpha=0.1,
        fg_colour=0xFFFF00,
        fg_alpha=0.7,
        x=924, y=120,
        radius=70,
        thickness=4,
        angle=0
    },
    {
        name='time',
        arg='+%M',
        max=60,
        bg_colour=0xE3E3E3,
        bg_alpha=0.1,
        fg_colour=0x00CD00,
        fg_alpha=0.7,
        x=924, y=120,
        radius=64,
        thickness=7,
        angle=0 
    },
    {
        name='time',
        arg='+%H',
        max=24,
        bg_colour=0xE3E3E3,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.7,
        x=924, y=120,
        radius=52,
        thickness=14,
        angle=0 
    },
 
}
 
require 'cairo'
 
function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
 
function draw_ring(t, pt)
    if conky_window==nil then return end
    local w,h=conky_window.width,conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual,w,h)
 
    cr=cairo_create(cs)
 
    local xc,yc,ring_r,ring_w,angle=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
 
    local angle_0=angle*(2*math.pi/360)-math.pi/2
    local t_arc=t*2*math.pi
 
    -- Draw background ring
 
    cairo_arc(cr,xc,yc,ring_r,0,2*math.pi)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
 
    -- Draw indicator ring
 
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
 
    cairo_destroy(cr)
    cr = nil
end
 
function conky_cairo_cleanup()
    cairo_surface_destroy(cs)
    cs = nil
end
 
function conky_ring_stats()
    local function setup_rings(pt)
        local str=''
        local value=0
 
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
 
        value=tonumber(str)
        pct=value/pt['max']
 
        draw_ring(pct,pt)
    end
 
    -- Check that Conky has been running for at least 5s
 
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
 
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(settings_table[i])
        end
    end
end
```capture my desktop :
_[IMG]http://img80.imageshack.us/img80/5161/screenshotli.png%5D%5Bimg=http://img80.imageshack.us/img80/5161/screenshotli.th.png[/IMG]_[[IMG]http://img80.imageshack.us/img80/5161/screenshotli.th.png[/IMG]]("http://img80.imageshack.us/img80/5161/screenshotli.png")

please help and thanks for support.

regards,
Maulbox :)

---

### Post by londonali1010 on 2009-10-16
Hi Maulbox...

In your rings.lua, the first ring (with all the comments in the settings_table) has a centre of x=120, y=100.  All the others have x=100, y=100.  Looks like you just missed that one!

---

### Post by maulbox on 2009-10-16
found it, i thoug below its not part of the script :)

```

settings_table = {
    {
        -- Edit this table to customise your rings.
        -- You can create more rings simply by adding more elements to settings_table.
        -- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
        name='cpu',
        -- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
        arg='cpu0',
        -- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
        max=100,
        -- "bg_colour" is the colour of the base ring.
        bg_colour=0xCDCDC1,
        -- "bg_alpha" is the alpha value of the base ring.
        bg_alpha=0.5,
        -- "fg_colour" is the colour of the indicator part of the ring.
        fg_colour=0xFF0000,
        -- "fg_alpha" is the alpha value of the indicator part of the ring.
        fg_alpha=0.8,
        -- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
        x=100, y=120,
        -- "radius" is the radius of the ring.
        radius=91,
        -- "thickness" is the thickness of the ring, centred around the radius.
        thickness=10,
        -- "angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
        angle=90
```

---

### Post by searchOne on 2009-10-20
Hi maulbox,
are the Fonts which are used in my Conky script also installed with you? :confused:
Font >LiberationMono, >DTPDingbats or >Zekton?

If not, please Installing only the missing Fonts and tries it once more!

---

### Post by searchOne on 2009-10-21
Hi all,
I have a question: 
 is it possible with one ".conkyrc" two lua-cairo script to start? :confused:

---

### Post by dk75 on 2009-10-21
from before "TEXT" - you could load as many scripts as you like but you could start only two functions. One by "lua_draw_hook_pre" and another by "lua_draw_hook_post".
After "TEXT" you could start as many LUA function as you like by "${lua function_name}" but it is for text only LUA's that will give back some text to show by Conky.

But... it is some workaround.
Gather as many LUA scripts like "rings.lua", "airclock.lua" and some other graphical features in "~/conky/lua" directory.
Then make one "main.lua" script with this:
```

do
	package.path = "/home/your_user_name/conky/lua/?.lua" -- path to my conky-lua directory where Conky LUA scripts are stored
	require 'cairo'
	require 'airclock'
	require 'rings'

	function main()
		airclock-function(100,100)
		ring-function(200,200,25,50)
	end
end

```
and call it with "lua_draw_hook_pre main"

---

### Post by londonali1010 on 2009-10-21
> **dk75 said:**
> from before "TEXT" - you could load as many scripts as you like but you could start only two functions. One by "lua_draw_hook_pre" and another by "lua_draw_hook_post".
After "TEXT" you could start as many LUA function as you like by "${lua function_name}" but it is for text only LUA's that will give back some text to show by Conky.

But... it is some workaround.
Gather as many LUA scripts like "rings.lua", "airclock.lua" and some other graphical features in "~/conky/lua" directory.
Then make one "main.lua" script with this:
```

do
	package.path = "/home/your_user_name/conky/lua/?.lua" -- path to my conky-lua directory where Conky LUA scripts are stored
	require 'cairo'
	require 'airclock'
	require 'rings'

	function main()
		airclock-function(100,100)
		ring-function(200,200,25,50)
	end
end

```
and call it with "lua_draw_hook_pre main"

You can also use my Conky Widgets script, if you want to run multiple widgets at once...You copy in code blocks of the widgets you want and call them with just the single call to the widgets function.  More info on the [Conky Blog]("http://blog.conky.be/2009/10/19/widgets-in-conky-it-can-be-done/"). :)

---

### Post by searchOne on 2009-10-22
> **dk75 said:**
> from before "TEXT" - you could load as many scripts as you like but you could start only two functions. One by "lua_draw_hook_pre" and another by "lua_draw_hook_post".
After "TEXT" you could start as many LUA function as you like by "${lua function_name}" but it is for text only LUA's that will give back some text to show by Conky.

But... it is some workaround.
Gather as many LUA scripts like "rings.lua", "airclock.lua" and some other graphical features in "~/conky/lua" directory.
Then make one "main.lua" script with this:
```

do
    package.path = "/home/your_user_name/conky/lua/?.lua" -- path to my conky-lua directory where Conky LUA scripts are stored
    require 'cairo'
    require 'airclock'
    require 'rings'

    function main()
        airclock-function(100,100)
        ring-function(200,200,25,50)
    end
end

```and call it with "lua_draw_hook_pre main"

Hi all,
thanks for Help @dk75 and londonali1010!
But since I'm still a problem! It is here that time the most important data: :confused:

.conkyrc
```
...
lua_load ~/conky/lua/main.lua
lua_draw_hook_pre main

TEXT
....

```main.lua
```
do
    package.path = "/home/search/conky/lua/?.lua"
    require 'cairo'
    require 'rings'
    require 'ring_top'

    function main()
        rings-function(200,200,25,50)
        ring_top-function(100,100)
    end
end
```Question: What kind of values the individual functions are behind 
...
ring function (200,200,25,50)?

This error message I get when I start Conky:
```
...
Conky: llua_do_call: function conky_main execution failed: attempt to call a nil value
...

```What could this mean? :confused:

The rings.lua is londonali1010's ring Skript, an ring_top.lua is this
[http://www.gnome-look.org/content/show.php?content=111096](http://www.gnome-look.org/content/show.php?content=111096)

---

### Post by dk75 on 2009-10-22
> **searchOne said:**
> Question: What kind of values the individual functions are behind 
...
ring function (200,200,25,50)?
dummy value - I don't know londonali1010 LUA scripts so I don't know what values it takes ;PPPp
Just improvised

---

### Post by londonali1010 on 2009-10-22
> **searchOne said:**
> Hi all,
thanks for Help @dk75 and londonali1010!
But since I'm still a problem! It is here that time the most important data: :confused:

.conkyrc
```
...
lua_load ~/conky/lua/main.lua
lua_draw_hook_pre main

TEXT
....

```main.lua
```
do
    package.path = "/home/search/conky/lua/?.lua"
    require 'cairo'
    require 'rings'
    require 'ring_top'

    function main()
        rings-function(200,200,25,50)
        ring_top-function(100,100)
    end
end
```Question: What kind of values the individual functions are behind 
...
ring function (200,200,25,50)?

This error message I get when I start Conky:
```
...
Conky: llua_do_call: function conky_main execution failed: attempt to call a nil value
...

```What could this mean? :confused:

The rings.lua is londonali1010's ring Skript, an ring_top.lua is this
[http://www.gnome-look.org/content/show.php?content=111096](http://www.gnome-look.org/content/show.php?content=111096)

> **dk75 said:**
> dummy value - I don't know londonali1010 LUA scripts so I don't know what values it takes ;PPPp
Just improvised

Try this instead:
```
do
    package.path = "~/conky/lua/?.lua"
    require 'cairo'
    require 'rings'
    require 'ring_top'

    function main()
        conky_ring_stats() -- calls the rings script
        conky_pie_time() -- calls the pies script
    end
end
```

From what I can tell in this method, you want to call the main function of the Rings script and the Pies script; the names of them are as above.  I hope this helps...I've not tried this method myself :)

---

### Post by searchOne on 2009-10-23
Hi you two! 
Thanks for your help, but it is not still running. 
There appears no rings, and the error in the console is still the same! :(](*,)

---

### Post by dk75 on 2009-10-23
change "function main()" to "function conky_main()" and check

---

### Post by Rob2687 on 2009-10-23
How can I define a cairo_text_extents_t variable?

I've tried **local cairo_text_extents_t te** but it just throws that nil error.
> Conky: llua_do_call: function conky_widgets execution failed: attempt to call a nil value



I trying to use the text extents functions in Cairo. Probably going about it wrong.

---

### Post by searchOne on 2009-10-24
> **dk75 said:**
> change "function main()" to "function conky_main()" and check

No change!
It will not run. Still the same error, and no rings!

---

### Post by searchOne on 2009-10-24
Have this error on conky-lua from file: rings.lua

```
Conky: llua_do_call: function conky_ring_stats execution failed: /home/search/conky/lua/rings.lua:242: attempt to perform arithmetic on local 'value' (a nil value)

```:confused:

Line 242: pct=value/pt['max']

---

### Post by londonali1010 on 2009-10-24
> **searchOne said:**
> Have this error on conky-lua from file: rings.lua

```
Conky: llua_do_call: function conky_ring_stats execution failed: /home/search/conky/lua/rings.lua:242: attempt to perform arithmetic on local 'value' (a nil value)

```:confused:

Line 242: pct=value/pt['max']

Ah, well first of all, make sure you have
```
if value == nil then value = 0 end
pct = value/pt['max']
```

If that doesn't work, have you tried the [Conky Widgets]("http://conky.linux-hardcore.com/?page_id=3331") script? It does a similar thing...

---

### Post by searchOne on 2009-10-24
> **londonali1010 said:**
> Ah, well first of all, make sure you have
```
if value == nil then value = 0 end
pct = value/pt['max']
```If that doesn't work, have you tried the [Conky Widgets]("http://conky.linux-hardcore.com/?page_id=3331") script? It does a similar thing...

Hi londonali1010,
thanks, that works! :KS

---

### Post by londonali1010 on 2009-10-24
> **searchOne said:**
> Hi londonali1010,
thanks, that works! :KS

Yay! :guitar:

---

### Post by dk75 on 2009-10-24
> **searchOne said:**
> 
The rings.lua is londonali1010's ring Skript, an ring_top.lua is this
[http://www.gnome-look.org/content/show.php?content=111096](http://www.gnome-look.org/content/show.php?content=111096)

Hm... where for the sake of God do you have "ring_top.lua" on this page? I don't see it so if it's not here how do you think it should work? It should be either "cairo-pie" or "cairo-pie-londonali1010" unless you renamed it to "ring_top.lua"

And in "package.path" character "~" as home directory alias don't work - it needs full path, like "/home/search/conky/lua/?.lua"

---

### Post by searchOne on 2009-10-25
> **dk75 said:**
> Hm... where for the sake of God do you have "ring_top.lua" on this page? I don't see it so if it's not here how do you think it should work? It should be either "cairo-pie" or "cairo-pie-londonali1010" unless you renamed it to "ring_top.lua"

And in "package.path" character "~" as home directory alias don't work - it needs full path, like "/home/search/conky/lua/?.lua"

Hi dk75,
no, it does not matter what name has the file. At the beginning I had used the old name. And with the ~ or 
/home/search/... does not matter which option is used. :(
I will now test all our things with the widgets of londonali1010, then I call again! Thank you!

---

### Post by dk75 on 2009-10-25
strange, it working... not as expected but working
```

conky -c ~/.conky/.conkyrc-test12
Conky: desktop window (16000a3) is subwindow of root window (13c)
Conky: window type - override
Conky: drawing to created window (0x5c00001)
Conky: drawing to double buffer
Conky: top needs arguments
Conky: llua_do_call: function conky_main execution failed: /home/dk75/.conky/lua/cairo-pie.lua:142: bad argument #3 to 'format' (string expected, got nil)
Conky: llua_do_call: function conky_main execution failed: /home/dk75/.conky/lua/cairo-pie.lua:142: bad argument #3 to 'format' (string expected, got nil)
Conky: llua_do_call: function conky_main execution failed: /home/dk75/.conky/lua/cairo-pie.lua:142: bad argument #3 to 'format' (string expected, got nil)
Conky: llua_do_call: function conky_main execution failed: /home/dk75/.conky/lua/cairo-pie.lua:142: bad argument #3 to 'format' (string expected, got nil)
Conky: llua_do_call: function conky_main execution failed: /home/dk75/.conky/lua/cairo-pie.lua:142: bad argument #3 to 'format' (string expected, got nil)
Conky: llua_do_call: function conky_main execution failed: /home/dk75/.conky/lua/cairo-pie.lua:142: bad argument #3 to 'format' (string expected, got nil)
Conky: llua_do_call: function conky_main execution failed: /home/dk75/.conky/lua/rings.lua:239: bad argument #3 to 'format' (string expected, got nil)
^CConky: received SIGINT or SIGTERM to terminate. bye!

```


/home/dk75/.conky/lua/main.lua
```

do
    package.path = "/home/dk75/.conky/lua/?.lua"
    require 'cairo'
    require 'rings'
    require 'cairo-pie'

    function conky_main()
        conky_ring_stats() -- calls the rings script
        conky_pie_time() -- calls the pies script
    end
end

```

---

### Post by londonali1010 on 2009-10-25
> **Rob2687 said:**
> How can I define a cairo_text_extents_t variable?

I've tried **local cairo_text_extents_t te** but it just throws that nil error.



I trying to use the text extents functions in Cairo. Probably going about it wrong.

I'm trying to figure it out too...I'm trying to manipulate some text in Cairo, but without the cairo_text_extents functionality, I can only use bottom-left anchoring and it doesn't really look great.  Been doing a lot of research, and it seems like there's something funny with Lua not recognising the typedef cairo_text_extents_t.  I haven't been able to figure out how to force a variable to be of that type either, because Lua uses dynamic type definitions.  That said, it looks like the Cairo typedefs are included in the tolua package, so I dunno.

Wow, it almost sounds like I have a freakin' clue what I'm talking about!

---

### Post by lmcadory on 2009-10-26
I am having all kinds of trouble with Conky.

I have the latest Conky 1.7.2 that I installed from Synaptic. I installed the [all] version so everything should be enabled. 

I tried to run a simple conkyrc file and .lua file here:


conkytestrc

```
alignment top_left
background no
border_inner_margin 0
border_outer_margin 0
cpu_avg_samples 2
default_color 94959C
default_outline_color 94959C
default_shade_color 94959C
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
gap_x 300
gap_y 40
maximum_width 450
max_port_monitor_connections 64
max_specials 512
max_user_text 16384
minimum_size 450 450
net_avg_samples 2
no_buffers yes
out_to_console no
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type normal
own_window yes
update_interval 0.4
uppercase no
use_spacer none
use_xft yes
xftalpha 0.8
xftfont  Purisa:size=7
 
# -- Lua Load -- #
lua_load ~/Conky/scripts/Rings.lua
lua_draw_hook_pre Rings
 
TEXT
${color 16bfff}${offset 302}${voffset 31}${font Purisa:size=12} ${time %H}
${offset 343}${voffset 21}${font Purisa:size=12} ${time %M}
${offset 365}${voffset 32}${font Purisa:size=12} ${time %S}
${offset 360}${voffset 33}${font Purisa:size=12} ${time %a}
${offset 355}${voffset 33}${font Purisa:size=12} ${time %d}
${offset 320}${voffset 27}${font Purisa:size=12} ${time %b}
${offset 273}${voffset 10}${font Purisa:size=12} ${time %y}
${font Purisa:size=8}${color ffffff}${offset 219}${voffset -125}.Wireless
${offset 219}${voffset 4}.Used Space
${offset 219}${voffset 2}.Battery
${offset 219}${voffset 1}.CPU
${offset 219}${voffset 0}.Memory
```


Rings.lua (I renamed the orignal clock_rings)

```
--[[
Clock Rings by londonali1010 (2009)
 
This script draws percentage meters as rings, and also draws clock hands if you want! It is fully customisable; all options are described in the script. This script is based off a combination of my clock.lua script and my rings.lua script.
 
IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.
 
To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
	lua_load ~/scripts/clock_rings.lua
	lua_draw_hook_pre clock_rings
 
Changelog:
+ v1.0 -- Original release (30.09.2009)
]]
 
settings_table = {
	{
		name='cpu',
		arg='cpu0',
		max=100,
		bg_colour=0x016BFF,
		bg_alpha=0,
		fg_colour=0x016BFF,
		fg_alpha=0.8,
		x=195, y=195,
		radius=137.5,
		thickness=15,
		start_angle=-230,
		end_angle=40
	},
	{
		name='memperc',
		arg='',
		max=100,
		bg_colour=0x016BFF,
		bg_alpha=0.1,
		fg_colour=0x016BFF,
		fg_alpha=0.5,
		x=195, y=195,
		radius=157,
		thickness=13,
		start_angle=45,
		end_angle=315
	},
	{
		name='fs_used_perc',
		arg='/',
		max=100,
		bg_colour=0x016BFF,
		bg_alpha=0,
		fg_colour=0x016BFF,
		fg_alpha=0.5,
		x=195, y=195,
		radius=100,
		thickness=20,
		start_angle=-250,
		end_angle=20
	},
	{
		name='battery_percent',
		arg='BAT1',
		max=100,
		bg_colour=0xFF0000,
		bg_alpha=0.4,
		fg_colour=0x016BFF,
		fg_alpha=0.5,
		x=195, y=195,
		radius=120,
		thickness=10,
		start_angle=-50,
		end_angle=210
	},
	{
		name='time',
		arg='%I',
		max=12,
		bg_colour=0x016BFF,
		bg_alpha=0.3,
		fg_colour=0xFFFFFF,
		fg_alpha=0.8,
		x=320, y=46,
		radius=28,
		thickness=5,
		start_angle=0,
		end_angle=360
	},
	{
		name='time',
		arg='%M',
		max=60,
		bg_colour=0x016BFF,
		bg_alpha=0.3,
		fg_colour=0xFFFFFF,
		fg_alpha=0.8,
		x=362, y=93,
		radius=28,
		thickness=5,
		start_angle=0,
		end_angle=360
	},
	{
		name='time',
		arg='%S',
		max=60,
		bg_colour=0x016BFF,
		bg_alpha=0.3,
		fg_colour=0xFFFFFF,
		fg_alpha=0.8,
		x=386, y=150,
		radius=28,
		thickness=5,
		start_angle=0,
		end_angle=360
	},
	{
		name='time',
		arg='%u',
		max=7,
		bg_colour=0x016BFF,
		bg_alpha=0.3,
		fg_colour=0xFFFFFF,
		fg_alpha=0.8,
		x=390, y=211,
		radius=28,
		thickness=5,
		start_angle=0,
		end_angle=360
	},
	{
		name='time',
		arg='%d',
		max=31,
		bg_colour=0x016BFF,
		bg_alpha=0.3,
		fg_colour=0xFFFFFF,
		fg_alpha=0.8,
		x=375, y=272,
		radius=28,
		thickness=5,
		start_angle=0,
		end_angle=360
	},
	{
		name='time',
		arg='%m',
		max=12,
		bg_colour=0x016BFF,
		bg_alpha=0.3,
		fg_colour=0xFFFFFF,
		fg_alpha=0.8,
		x=343, y=325,
		radius=28,
		thickness=5,
		start_angle=0,
		end_angle=360
	},
	{
		name='time',
		arg='%g',
		max=99,
		bg_colour=0x016BFF,
		bg_alpha=0.3,
		fg_colour=0xFFFFFF,
		fg_alpha=0.8,
		x=292, y=363,
		radius=28,
		thickness=5,
		start_angle=0,
		end_angle=360
	},
	{
		name='wireless_link_qual_perc',
		arg='wlan0',
		max=100,
		bg_colour=0x016BFF,
		bg_alpha=0.1,
		fg_colour=0x016BFF,
		fg_alpha=0.9,
		x=195, y=195,
		radius=80,
		thickness=12.5,
		start_angle=-70,
		end_angle=200
	},
}
 
-- Use these settings to define the origin and extent of your clock.
 
clock_r=125
 
-- "clock_x" and "clock_y" are the coordinates of the centre of the clock, in pixels, from the top left of the Conky window.
 
clock_x=195	
clock_y=195
 
show_seconds=true
 
require 'cairo'
 
function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
 
function draw_ring(cr,t,pt)
	local w,h=conky_window.width,conky_window.height
 
	local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
 
	local angle_0=sa*(2*math.pi/360)-math.pi/2
	local angle_f=ea*(2*math.pi/360)-math.pi/2
	local t_arc=t*(angle_f-angle_0)
 
	-- Draw background ring
 
	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
 
	-- Draw indicator ring
 
	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
end
 
function draw_clock_hands(cr,xc,yc)
	local secs,mins,hours,secs_arc,mins_arc,hours_arc
	local xh,yh,xm,ym,xs,ys
 
	secs=60-os.date("%S")	
	mins=60-os.date("%M")
	hours=12-os.date("%I")
 
	secs_arc=(2*math.pi/60)*secs
	mins_arc=(2*math.pi/60)*mins+secs_arc/60
	hours_arc=(2*math.pi/12)*hours+mins_arc/12
 
	-- Draw hour hand
 
	xh=xc+0.7*clock_r*math.sin(hours_arc)
	yh=yc-0.7*clock_r*math.cos(hours_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xh,yh)
 
	cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
	cairo_set_line_width(cr,5)
	cairo_set_source_rgba(cr,0,0,1,0.6)
	cairo_stroke(cr)
 
	-- Draw minute hand
 
	xm=xc+clock_r*math.sin(mins_arc)
	ym=yc-clock_r*math.cos(mins_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xm,ym)
 
	cairo_set_line_width(cr,3)
	cairo_set_source_rgba(cr,0,0,1,0.7)
	cairo_stroke(cr)
 
	-- Draw seconds hand
 
	if show_seconds then
		xs=xc+1.1*clock_r*math.sin(secs_arc)
		ys=yc-1.1*clock_r*math.cos(secs_arc)
		cairo_move_to(cr,xc,yc)
		cairo_line_to(cr,xs,ys)
 
		cairo_set_line_width(cr,1)
		cairo_set_source_rgba(cr,0,0,1,0.8)
		cairo_stroke(cr)
	end
end
 
function conky_clock_rings()
	local function setup_rings(cr,pt)
		local str=''
		local value=0
 
		str=string.format('${%s %s}',pt['name'],pt['arg'])
		str=conky_parse(str)
 
		value=tonumber(str)
		pct=value/pt['max']
 
		draw_ring(cr,pct,pt)
	end
 
	-- Check that Conky has been running for at least 5s
 
	if conky_window==nil then return end
	local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
 
	local cr=cairo_create(cs)	
 
	local updates=conky_parse('${updates}')
	update_num=tonumber(updates)
 
	if update_num>5 then
		for i in pairs(settings_table) do
			setup_rings(cr,settings_table[i])
		end
	end
 
	draw_clock_hands(cr,clock_x,clock_y)
end
```

When I run the file I get 

```
Conky: desktop window (16000a7) is subwindow of root window (8c)
Conky: window type - normal
Conky: drawing to created window (0x5800001)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_Rings execution failed: attempt to call a nil value

```


The display shows everything but the hands of the clock.
Is their something I am doing wrong??

---

### Post by londonali1010 on 2009-10-27
Even though you renamed the *file* to be rings.lua, the "main" function of the script is still conky_clock_rings(), so you need to use either:
```
lua_draw_hook_pre clock_rings
```
or
```
lua_draw_hook_pre conky_clock_rings
```
(both do the same thing).

Either that, or you can rename the function conky_clock_rings() to be conky_rings().

HTH!

---

### Post by dk75 on 2009-11-01
OK.
About **text_extents** in LUA and Cairo.
It seems that Conky developers took old unmaintained luacairo bindings from [http://luaforge.net/projects/luacairo/](http://luaforge.net/projects/luacairo/)
This needs tolua++ and it seems to be faulty.

But, there is another LuaCairo bindings that working perfectly.
[Hakk&#305; Do&#287;usan LuaCairo](http://www.dynaset.org/dogusanh/pgluacairo.html)
That nifty code don't need tolua++ and works perfectly.

There's LUA code to run as "lua cairo_test2.lua" in terminal:
```

local cairo = require "lcairo"
local CAIRO = cairo

w = 320
h = 240
outfile = 'cairo_test2.png'

cs = cairo.image_surface_create(CAIRO.FORMAT_RGB24, w, h)

cr = cairo.create(cs)

cairo.set_source_rgb(cr, 1, 1, 1)
cairo.paint(cr)

cairo.set_source_rgb(cr, 0, 0, 0)
cairo.select_font_face (cr, "Sans", CAIRO.FONT_SLANT_NORMAL, CAIRO.FONT_WEIGHT_NORMAL)
cairo.set_font_size(cr, w/6)
text = "Cairo Text"
extents = cairo.TextExtents()
cairo.text_extents(cr, text, extents)
cairo.move_to(cr, w-extents.x_advance, h-extents.y_advance)
cairo.show_text(cr, text)
cairo.stroke(cr)

cairo.surface_write_to_png(cs, outfile)

```

In atachements are PNG result image and "LuaCairo" for 32bit and 64bit that needs to be copied to "/usr/local/lua/5.1/" ( 64bit version was compiled on my computer so it could not work for system other that Ubuntu 9.04 _x86-64 )

---

### Post by londonali1010 on 2009-11-01
Have you pinged that to Brenden & Co? Seems like something that could be fixed in the next release :)

---

### Post by dk75 on 2009-11-01
Oh no... It have a small little problem thought... "cairo_xlib_surface_create" is not implemented so can't open Conky window surface to draw on it.

---

### Post by londonali1010 on 2009-11-01
> **dk75 said:**
> Oh no... It have a small little problem thought... "cairo_xlib_surface_create" is not implemented so can't open Conky window surface to draw on it.

Well, maybe it'll just be a workaround, then.  Normal Cairo bindings enabled, but you should still be able to require "lcairo" as you have, and use a combo of both...?  I'll give it a try tonight perhaps!

---

### Post by dk75 on 2009-11-01
tryed it already and it not work - "can't call cairo_xlib_surface_create NIL value"

But maybe Conky devs could persuade Hakki to add that function.

---

### Post by 5BallJuggler on 2009-11-03
I really like this idea, 

[IMG]http://u1.imgupload.co.uk/1256515200/8d8e_screenshot_2.png[/IMG]

but I can't seem to make it work, does anyone have any ideas, 
I "Borrowed" the pie script from [http://ubuntuforums.org/showthread.php?p=8166526#post8166526]("http://ubuntuforums.org/showthread.php?p=8166526#post8166526")

```
-- xc,yc - center of the pie
-- r - radius of the pie

require 'cairo'

function pie_rings (xc, yc, r)

	pat = cairo_pattern_create_radial (xc, yc, 0.2*r, xc,  yc, r);
	cairo_pattern_add_color_stop_rgba (pat, 0.1, 1, 1, 1, 0);
	cairo_pattern_add_color_stop_rgba (pat, 1.0, 1, 1, 1, 0.1);
	cairo_set_source (cr, pat);
	cairo_arc (cr, xc, yc, r, 0, 2 * math.pi);
	cairo_fill (cr);
	cairo_pattern_destroy (pat);


	cairo_set_font_size (cr, 10)
	cairo_select_font_face (cr, "LCDMono",
				CAIRO_FONT_SLANT_NORMAL,
				CAIRO_FONT_WEIGHT_NORMAL)	
	cairo_set_line_width (cr, 2.0)

	-- Show total mem usage
	local str1 = conky_parse(string.format('${mem}'))
	local str2 = string.match(str1, "(%d+)")
	local str3 = string.match(str1, "(%a+)")

	cairo_set_source_rgba(cr, 1, 1, 1, 1)
	cairo_move_to (cr, xc-9, yc-1)
	cairo_show_text (cr, str2)
	cairo_move_to (cr, xc-9, yc+9)
	cairo_show_text (cr, str3)
	cairo_stroke(cr)

	-- Get top mem usage
	local str1 = conky_parse(string.format('${mem}'))
	local mem = tonumber(string.match(str1, "(%d+)"))
	local str1 = conky_parse(string.format('${memperc}'))
	local mempct = tonumber(string.match(str1, "(%d+)"))
	
	-- Draw pie
	local angle = -90
	local angle2 = 0
	local tro = 4		-- Text rotational offset (degrees)
	local maxprocesses = 7
	local maxstrlen = 8

	for process = 1, maxprocesses do

		cairo_save(cr)
	
		-- Get top process memory usage
		local str2 = conky_parse(string.format('${top_mem mem %i}', tonumber(process)))
		local mem_process = tonumber(str2)
		local procpct = mem_process / mempct
		angle2 = angle + (procpct*360)

		if angle2 > 260 then
			cairo_restore(cr)
			break
		end	

		-- Get top process name
		local str2 = conky_parse(string.format('${top_mem name %i} ', tonumber(process)))
		local index = string.find(str2,' ')
		
		if (index == nil) then
			cairo_restore(cr)
			break
		elseif (index > maxstrlen) then
			str2 = string.sub(str2, 0, maxstrlen)
		end

		-- Draw pie outline
		cairo_set_source_rgba(cr, 1, 1, 1, 0.2)		
		cairo_arc_negative (cr, xc, yc, 0.2*r, angle2*(math.pi/180), angle*(math.pi/180));			
		cairo_arc (cr, xc, yc, r, angle*(math.pi/180), angle2*(math.pi/180));	
--		cairo_close_path(cr)
		cairo_stroke(cr)

		-- Draw text
		cairo_set_source_rgba(cr, 1, 1, 1, 0.5)	
		cairo_move_to(cr, xc, yc)
		cairo_rotate(cr, (angle2-((angle2-angle)/2)+tro)*(math.pi/180))
--		cairo_show_text (cr, '    '..(procpct*100))
		if (index > maxstrlen) then
			cairo_show_text (cr, '      '..str2..'..')
		else
			cairo_show_text (cr, '      '..str2)
		end		

		angle = angle2 + 3

		cairo_stroke(cr)
		cairo_restore(cr)
	end

	if (angle < 264) then
		angle2 = 267
		cairo_set_source_rgba(cr, 1, 1, 1, 0.2)	
		cairo_arc_negative (cr, xc, yc, 0.2*r, angle2*(math.pi/180), angle*(math.pi/180));
		cairo_arc (cr, xc, yc, r, angle*(math.pi/180), angle2*(math.pi/180));	
--		cairo_close_path(cr)
		cairo_stroke(cr)
		
		if ((angle2 - angle) > 20) then
			cairo_set_source_rgba(cr, 1, 1, 1, 0.5)	
			cairo_move_to(cr, xc, yc)
			cairo_rotate(cr, (angle2-((angle2-angle)/2)+tro+2)*(math.pi/180))
			cairo_show_text (cr, '      '..'other')
			cairo_stroke(cr)
		end
	end
end
```

This is how I'm calling it

```
alignment top_left
background no
border_inner_margin 0
border_outer_margin 0
cpu_avg_samples 2
default_color 94959C
default_outline_color 94959C
default_shade_color 94959C
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
gap_x 100
gap_y 300
maximum_width 200
max_port_monitor_connections 64
max_specials 512
max_user_text 16384
minimum_size 0 0
net_avg_samples 2
no_buffers yes
out_to_console no
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type normal
own_window yes
update_interval 10
uppercase no
use_spacer none
use_xft yes
xftalpha 0.3
xftfont Purisa:size=7

# -- Lua Load -- #
lua_load ~/scripts/pie_rings.lua
lua_draw_hook_pre pie_rings

TEXT

```

---

### Post by pbeesley on 2009-11-04
Question....I have some lua rings....can I plot text onto them so it rotates round as they do? 

If I'm not making sense let me know and I'll make a mock up

---

### Post by londonali1010 on 2009-11-04
> **pbeesley said:**
> Question....I have some lua rings....can I plot text onto them so it rotates round as they do? 

If I'm not making sense let me know and I'll make a mock up

Can you do a mock-up, please?  I can already think of a few different ways you might mean...

Generally speaking, yes, you can plot text anywhere you like, in whatever rotation you want, but *how* is another question! ):P

---

### Post by pbeesley on 2009-11-04
:D ask and thou shall recieve. 

here's what I would like to have. With a seperate ring for ram cpu etc with the smae text on the rings.

Thanks

---

### Post by Rob2687 on 2009-11-05
I've thought about doing something like that. I'm not sure if it's possible to get text drawing to follow a path with Cairo.

One way that would probably work is to render a character, rotate and repeat but that could get pretty slow.

---

### Post by londonali1010 on 2009-11-05
Yeah, I'm not aware of being able to make text follow a path; you'd probably have to split the string to print into an array, and then rotate each letter around...

You might check the imlib2 text options as well, as at first glance they look a little better than Cairo's text, and I know that you can use imlib2 and Cairo to draw to the same surface...

---

### Post by sknud on 2009-11-05
Trying to get this rings script to work. No errors and no rings.

conkyrc:
```
 background no
    use_xft yes
    xftfont Eurostar Regular Extended:size=10
    xftalpha 0.1
    update_interval 1.0
    total_run_times 0
    own_window yes
    own_window_transparent yes
    own_window_type override
    #own_window_type normal
    #own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color white
    default_shade_color white
    default_outline_color white
    alignment top_left
    gap_x 0
    gap_y 0
    no_buffers yes
    uppercase yes
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer right
    text_buffer_size 256

    color1 7F7F7F
    color2 CFCFCF
    color3 F7BD5F

    lua_load ~/.conky/conky_widgets.lua
    lua_draw_hook_pre widgets

    TEXT

```

conky_widgets.lua:
```
require 'cairo'

--[[ GRADIENT RING WIDGET ]]
--[[ Options (name, arg, max, colour, alpha, x, y, inner_radius, outer_radius, frac, thickness, start_angle, end_angle):
        "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
        "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
        "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
        "fg_colour" is the colour of the ring.
        "fg_alpha" is the alpha value of the ring.
        "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
        "inner_radius" is the inner radius of the ring.
        "outer_radius" is the outer radius of the ring.  
        "frac" determines the extent of the gradient around the ring - 2 implies the gradient fades halfway around the ring, 4 equals a quarter of the way, etc...      
        "thickness" is the thickness of the ring, centred around the radius.
        "start_angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
        "end_angle" is the ending angle of the ring, in degrees, clockwise from top. Value can be either positive or negative, but must be larger (e.g. more clockwise) than start_angle. ]]
     
function gradient_ring(cr, name, arg, max, fgc, fga, xc, yc, ring_i, ring_o, frac, t, sa, ea)
        local function rgb_to_r_g_b(colour,alpha)
            return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
        end
     
        local function draw_gradient_ring(pct)
            local angle_0=sa*(2*math.pi/360)-math.pi/2
            local angle_f=ea*(2*math.pi/360)-math.pi/2
            local pct_arc=pct*(angle_f-angle_0)
     
            for i = 1,max/frac do
                cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga*i/max)) --for flat shading of bars
        
                --local pat=cairo_pattern_create_linear(xc-ring_i*math.sin(angle_0+t_arc+2*math.pi*i/max),yc+ring_i*math.cos(angle_0+t_arc+2*math.pi*i/max),xc-ring_o*math.sin(angle_0+t_arc+2*math.pi*i/max),yc+ring_o*math.cos(angle_0+t_arc+2*math.pi*i/max))
                --cairo_pattern_add_color_stop_rgba(pat,0,rgb_to_r_g_b(fgc,0))
                --cairo_pattern_add_color_stop_rgba(pat,1,rgb_to_r_g_b(fgc,fga*i/max))
                --cairo_set_source(cr,pat) -- for gradient shading of bars
        
                cairo_move_to(cr,xc-ring_i*math.cos(angle_0+pct_arc+2*math.pi*i/max),yc-ring_i*math.sin(angle_0+pct_arc+2*math.pi*i/max))
                cairo_line_to(cr,xc-ring_o*math.cos(angle_0+pct_arc+2*math.pi*i/max),yc-ring_o*math.sin(angle_0+pct_arc+2*math.pi*i/max))
    
                cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
                cairo_set_line_width(cr,t)
                cairo_stroke(cr)
            end
        end
     
        local function setup_gradient_ring()
            local str = ''
            local value = 0
     
            str = string.format('${%s %s}', name, arg)
            str = conky_parse(str)
     
            value = tonumber(str)
            if value == nil then value = 0 end
            pct = value/max
     
            draw_gradient_ring(pct)
        end    
     
        local updates=conky_parse('${updates}')
        update_num=tonumber(updates)
     
        if update_num>5 then setup_gradient_ring() end
    end
     
--[[ END GRADIENT RING WIDGET ]]



function conky_widgets()
    if conky_window == nil then return end
    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)

    cr = cairo_create(cs)
    gradient_ring(cr, 'time', '%I', 12, 0xf7cd5f, 1.0, 580, 400, 100, 120, 2, 4, 0, 360)
    cairo_destroy(cr)

    cr = cairo_create(cs)
    gradient_ring(cr, 'time', '%M', 60, 0xffffff, 0.8, 580, 400, 130, 145, 2, 2, 0, 360)
    cairo_destroy(cr)
    
    cr = cairo_create(cs)
    gradient_ring(cr, 'time', '%S', 60, 0xffffff, 0.6, 580, 400, 160, 170, 2, 2, 0, 360)
    cairo_destroy(cr)
  
end


```

Can anyone see something wrong here?

---

### Post by londonali1010 on 2009-11-05
Do you have at the very least a " " after TEXT in your .conkyrc file? If you don't, it won't render a Conky window, so no display...

---

### Post by sknud on 2009-11-05
yes, ive tried with text also. and the text show up, still no rings though.

---

### Post by Rob2687 on 2009-11-05
> **5BallJuggler said:**
> I really like this idea, 

[IMG]http://u1.imgupload.co.uk/1256515200/8d8e_screenshot_2.png[/IMG]

but I can't seem to make it work, does anyone have any ideas, 
I "Borrowed" the pie script from [http://ubuntuforums.org/showthread.php?p=8166526#post8166526]("http://ubuntuforums.org/showthread.php?p=8166526#post8166526")




Add the following to the .lua file and call the conky_widgets function. You can set the position with xc,yc and the radius with r.

```
    function conky_widgets()
    	if conky_window == nil then return end
    	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	cr = cairo_create(cs)
	local w = conky_window.width
	local h = conky_window.height

	r = 75
	xc = w/2
	yc = h/2
	
	local updates=conky_parse('${updates}')
	update_num=tonumber(updates)
	
	if update_num>5 then
		pie_rings(xc, yc, r)
	end

    	cairo_destroy(cr)

    end
```

---

### Post by 5BallJuggler on 2009-11-06
> **Rob2687 said:**
> Add the following to the .lua file and call the conky_widgets function. You can set the position with xc,yc and the radius with r.

```
    function conky_widgets()
    	if conky_window == nil then return end
    	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	cr = cairo_create(cs)
	local w = conky_window.width
	local h = conky_window.height

	r = 75
	xc = w/2
	yc = h/2
	
	local updates=conky_parse('${updates}')
	update_num=tonumber(updates)
	
	if update_num>5 then
		pie_rings(xc, yc, r)
	end

    	cairo_destroy(cr)

    end
```

Thanks for the response.

Where do I add it, at the end, or in the middle after an "end" point, and am I calling the conky_widgets instead of conky_pie_rings?

Thanks
Phil

---

### Post by dk75 on 2009-11-06
> **londonali1010 said:**
> Do you have at the very least a " " after TEXT in your .conkyrc file? If you don't, it won't render a Conky window, so no display...

I have nothing after "TEXT" and Conky window is rendering... but i use:
```
minimum_size 600 600
maximum_width 600
```
for my "moving rings-clock" conkyrc

---

### Post by 5BallJuggler on 2009-11-06
> **5BallJuggler said:**
> Thanks for the response.

Where do I add it, at the end, or in the middle after an "end" point, and am I calling the conky_widgets instead of conky_pie_rings?

Thanks
Phil

Don't worry, fixed it! yay!!

Thanks All

---

### Post by biodiesel-bri on 2009-11-06
All I can say is WOW, Conky, and especially those rings are beautiful.  Thank you!!

Couple of things:

Here's how to get transparency working under KDE:
[http://conky.linux-hardcore.com/?page_id=2326]("http://conky.linux-hardcore.com/?page_id=2326")
Only the second option works for the KDE 4.3.2 released in 9.10.

I have been fiddling around with the rings script which mentions that you can only choose from like three things like cpu and free hd space.  But I was able to get a bunch more working including net up/down, the frequency of my GPU, and a dizzying array of goodness here:
[http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")

I'm in love with this thing.  Thank you again!!

---

### Post by dk75 on 2009-11-07
I've posted it month ago ( or more ) but FileDEN had problems and my files ( and other user that registered at 2006 ) was wiped out so here again:
[conky-cairo-rings.mp4[3MiB]](http://www.fileden.com/files/2006/12/11/497871/Ubuntu/Conky/conky-cairo-rings.mp4)

---

### Post by stinkeye on 2009-11-07
Hi londonali1010,
I'm using the conkyrc and lua script for the airclock from conkyhardcore and noticed that I was using a lot of memory.
Checked in system monitor and my air clock conky was using 261mb of memory.Is that normal?
Thanks.

---

### Post by jjcv on 2009-11-08
Hi londonali1010,

I have just been trying your Photo Album Widget.   Cut and pasted thw widget sample into my widget.lua and then added the appropriate line with the variables:

  cr = cairo_create(cs)
  photo_album(cr, '/home/john/Documents/Pictures/Roerich/', 150, 120,   300, 240, 10, 15) -- options: album_dir, xc, yc, w_max, h_max, t,   update_interval
  cairo_destroy(cr)

However when I try and run it I get and error on this line:
function photo_album(album_dir, xc, yc, w_max, h_max, t, update_interval)
    local function get_file_to_use()
        **num_files = tonumber(conky_parse("${execi ls -A " .. album_dir ..  " | wc -l}"))**
        if num_files == nil then num_files = 0 end
        if num_files == 0 then return "none" end

Here is the error message:

Conky: llua_do_call: function conky_widgets execution failed: /home/john/.conky/test/conky_widgets-2.lua:219: attempt to concatenate upvalue 'album_dir' (a userdata value)

It works perfectly if I don't use the widget and run it from its own lua file.  Not parsing the photo album directory. 

Any clues what I could look for?

---

### Post by londonali1010 on 2009-11-08
> **stinkeye said:**
> Hi londonali1010,
I'm using the conkyrc and lua script for the airclock from conkyhardcore and noticed that I was using a lot of memory.
Checked in system monitor and my air clock conky was using 261mb of memory.Is that normal?
Thanks.

It's about right, yeah.  It's because it's drawing an awful lot of gradients and things, probably once a second if you've got the seconds hand on.  The best way to drop the memory usage is to turn the seconds hand off and increase the update_interval of your Conky (up to every 30s).

---

### Post by londonali1010 on 2009-11-08
> **jjcv said:**
> Hi londonali1010,

I have just been trying your Photo Album Widget.   Cut and pasted thw widget sample into my widget.lua and then added the appropriate line with the variables:

  cr = cairo_create(cs)
  photo_album(cr, '/home/john/Documents/Pictures/Roerich/', 150, 120,   300, 240, 10, 15) -- options: album_dir, xc, yc, w_max, h_max, t,   update_interval
  cairo_destroy(cr)

However when I try and run it I get and error on this line:
function photo_album(album_dir, xc, yc, w_max, h_max, t, update_interval)
    local function get_file_to_use()
        **num_files = tonumber(conky_parse("${execi ls -A " .. album_dir ..  " | wc -l}"))**
        if num_files == nil then num_files = 0 end
        if num_files == 0 then return "none" end

Here is the error message:

Conky: llua_do_call: function conky_widgets execution failed: /home/john/.conky/test/conky_widgets-2.lua:219: attempt to concatenate upvalue 'album_dir' (a userdata value)

It works perfectly if I don't use the widget and run it from its own lua file.  Not parsing the photo album directory. 

Any clues what I could look for?

You'll need to be using Conky Widgets v1.1.  You can get it from [my DevArt account]("http://londonali1010.deviantart.com/art/Conky-Widgets-Script-141963883") (I haven't updated Conky Hardcore! yet...Sorry!). There are some slight differences in that script that you'll need for the photo_album widget block to work.

Please update your version, and let me know if you still get the same problem.

---

### Post by jjcv on 2009-11-08
> **londonali1010 said:**
> Please update your version, and let me know if you still get the same problem.

No, still the same error unfortunately.   For some reason the script gets an error for admin_dir.  My options are set like below.

         cr = cairo_create(cs)
        photo_album(cr, '/home/john/Documents/Pictures/Roerich/', 150, 120, 300, 240, 10, 15)
        cairo_destroy(cr)

It is probably something obvious that I am overlooking.

---

### Post by londonali1010 on 2009-11-08
> **jjcv said:**
> No, still the same error unfortunately.   For some reason the script gets an error for admin_dir.  My options are set like below.

         cr = cairo_create(cs)
        photo_album(cr, '/home/john/Documents/Pictures/Roerich/', 150, 120, 300, 240, 10, 15)
        cairo_destroy(cr)

It is probably something obvious that I am overlooking.

If you're using Conky Widgets v1.1, you can call the widgets using just:
```
photo_album('/home/john/Documents/Pictures/Roerich/', 150, 120, 300, 240, 10, 15)
```
leaving out the cairo_create and cairo_destroy lines, as I've called them globally now.  You can also leave out the cr argument to the function.

Sorry for the confusion; there's not a really good way to update this script!

Please let me know if you have any other issues :)

---

### Post by jjcv on 2009-11-08
> **londonali1010 said:**
> 
```
photo_album('/home/john/Documents/Pictures/Roerich/', 150, 120, 300, 240, 10, 15)
```


Thanks for that. Working now.  Taking the cr, out did the trick.

Love the things you are doing with conky etc.  Inspirational.:D

---

### Post by londonali1010 on 2009-11-08
^ Ah, thanks very much :)

---

### Post by enyaw_ecurb on 2009-11-10
Hi,

I posted the same issue at the screenshot-thread but I think it easily may get lost there :-)

I can't get images in cairo working. Supposedly it should work like this

```
	
image = cairo_image_surface_create_from_png ("xy.png")
cairo_set_source_surface (cr, image, 0, 0)
cairo_paint (cr)

```

alas it doesn't. It throws no error, it just doesn't paint anything. Everything else works, I can draw with cairo, but no images.

Suggestions? Wrong syntax?

Thanks!

---

### Post by dk75 on 2009-11-10
with this little fragment of script and without conkyrc it's hard to tell

---

### Post by slapfish on 2009-11-11
> **londonali1010 said:**
> 
[quote=BornTwisted;8039658]Hi Ali, a couple of things have crossed my mind about the display of the rings, is there an easy way to get the rings to work anti-clockwise and is it possible to make them ovals?
Probably! :)
There's a cairo_arc_negative() function, which is the same as the cairo_arc function, just counterclockwise. I'm not sure about drawing an oval/ellipse...[/quote]

First of all I want to express my great gratitude to you for all the good things on my desktop. I'm currently adjusting my conky on #! and soon enough I'm going to post it on #! forums. I'm in great need for an anticlockwise ring and I was wondering if I could add the proper code in the rings.lua you have posted to make it also draw anticlockwise. I try to do it myself but I get messed up and lost since I can't say I have any experience with all that. So my thought was to add a second sequence of variables like:

name2='cpu',
arg2='cpu1',
max2=100,
bg_colour2=0xFFFFFF,
bg_alpha2=0.1,
fg_colour2=0xFFFFFF,
fg_alpha2=0.5,
x2=100, y2=101.5,
radius2=82,
thickness2=25,
start_angle2=90,
end_angle2=270

and the proper code to draw an anticlockwise ring as well. Is it as simple as I'm thinking of it or is it simpler to load a new rings.lua with the cairo_arc_negative() instead of the cairo_arc() function?

if it's not a big trouble can you post the new code to be added under the "require 'cairo' " part of the code?

many thanks,
Dimitris

---

### Post by vitvic on 2009-11-13
Hi, this is my first message here on Ubuntuforums :). I've always searched solutions here, rather than asking myself. But now it is time to ask for some help.

I like Conky Rings a lot, but I'm having some troubles with it. What I want to know is: how can I establish the position of objects on a "z plane" other than the x and y planes in conky?

I have two pngs in my config:

${image /home/user/.conky/PNGs/1.png -p 0,0}
${image /home/user/.conky/PNGs/2.png -p 0,0}

and i want to put a ring between them. With the current config the ring is always on top:

---

### Post by londonali1010 on 2009-11-13
> **vitvic said:**
> Hi, this is my first message here on Ubuntuforums :). I've always searched solutions here, rather than asking myself. But now it is time to ask for some help.

I like Conky Rings a lot, but I'm having some troubles with it. What I want to know is: how can I establish the position of objects on a "z plane" other than the x and y planes in conky?

I have two pngs in my config:

${image /home/user/.conky/PNGs/1.png -p 0,0}
${image /home/user/.conky/PNGs/2.png -p 0,0}

and i want to put a ring between them. With the current config the ring is always on top:

Well, the problem is that they all draw to the same drawing surface, so theoretically, it should draw the ring first, then the .pngs on top (if you're using lua_draw_hook_pre to draw the rings).  Certainly, if you draw two images with $image, the second one will be drawn on top of the first, if they overlap.  Have you tried using Lua to draw your .pngs on your Conky window?

Also, can you post your .conkyrc and any scripts?

---

### Post by vitvic on 2009-11-13
Thank You for your quick reply and above all your patience/kindness ^^. Anyway, I've not tried using lua. Do you reckon it should solve the trick? How should I do that? With a new lua-script or using the existing ring-script?

This is the ring script, with only the cpu ring (I've deleted anything else):

```
--[[
Ring Meters by londonali1010 (2009)

This script draws percentage meters as rings. It is fully customisable; all options are described in the script.

IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.

To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
	lua_load ~/scripts/rings-v1.2.lua
	lua_draw_hook_pre ring_stats
	
Changelog:
+ v1.2 -- Added option for the ending angle of the rings (07.10.2009)
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]

settings_table = {
	{
		-- Edit this table to customise your rings.
		-- You can create more rings simply by adding more elements to settings_table.
		-- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
		name='time',
		-- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
		arg='%I.%M',
		-- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
		max=12,
		-- "bg_colour" is the colour of the base ring.
		bg_colour=0xffffff,
		-- "bg_alpha" is the alpha value of the base ring.
		bg_alpha=0.1,
		-- "fg_colour" is the colour of the indicator part of the ring.
		fg_colour=0xffffff,
		-- "fg_alpha" is the alpha value of the indicator part of the ring.
		fg_alpha=0.2,
		-- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
		x=-200, y=170,
		-- "radius" is the radius of the ring.
		radius=50,
		-- "thickness" is the thickness of the ring, centred around the radius.
		thickness=5,
		-- "start_angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
		start_angle=0,
		-- "end_angle" is the ending angle of the ring, in degrees, clockwise from top. Value can be either positive or negative, but must be larger (e.g. more clockwise) than start_angle.
		end_angle=360
	},
	{
		name='cpu',
		arg='cpu1',
		max=100,
		bg_colour=0xffffff,
		bg_alpha=0,
		fg_colour=0xAB0000,
		fg_alpha=0.9,
		x=-10, y=200,
		radius=320,
		thickness=36,
		start_angle=64,
		end_angle=116
	},
}

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(cr,t,pt)
	local w,h=conky_window.width,conky_window.height
	
	local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

	local angle_0=sa*(2*math.pi/360)-math.pi/2
	local angle_f=ea*(2*math.pi/360)-math.pi/2
	local t_arc=t*(angle_f-angle_0)

	-- Draw background ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
	
	-- Draw indicator ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
end

function conky_ring_stats()
	local function setup_rings(cr,pt)
		local str=''
		local value=0
		
		str=string.format('${%s %s}',pt['name'],pt['arg'])
		str=conky_parse(str)
		
		value=tonumber(str)
		pct=value/pt['max']
		
		draw_ring(cr,pct,pt)
	end

	if conky_window==nil then return end
	local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
	
	local cr=cairo_create(cs)	
	
	local updates=conky_parse('${updates}')
	update_num=tonumber(updates)
	
	if update_num>5 then
		for i in pairs(settings_table) do
			setup_rings(cr,settings_table[i])
		end
	end
end
```

and this is the conky config:

```
# Use Xft?
use_xft yes
xftfont saxMono:size=9
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
 own_window yes
 own_window_transparent yes
 own_window_type override
 #own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 400 400
maximum_width 400

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour 333333

# Text alignment, other possible values are commented
#alignment top_middle
alignment top_middle
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 325

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none
short_units yes
pad_percents 2
imlib_cache_size 0

# -- Lua Load -- #
lua_load /home/user/.conky/rings-v1.2.lua
lua_draw_hook_pre ring_stats

TEXT

${image /home/user/.conky/PNGs/1.png -p 0,0}
${image /home/user/.conky/PNGs/2.png -p 0,0}
```

while these are the pngs I'm actually using (maybe You can understand what I'm trying to do watching at them):

---

### Post by vitvic on 2009-11-15
> lua_draw_hook_pre ring_stats

I think that this line is the problem:

> This function, if defined, will be called by Conky through each iteration before drawing to the window. Requires X support. Takes any number of optional arguments. **Use this hook for drawing things on top of what Conky draws**. Conky puts 'conky_' in front of function_name to prevent accidental calls to the wrong function unless you place 'conky_' in front of it yourself.

I've tried some workarounds without success. I don't know how to draw a .png with Lua, so I've used your photo_album script to draw the top .png, but failed. It draws the .png on top, but seems to convert it to a .jpg (filling the empty spaces I've left on the picture).
Any suggestions?

Anyway, here a makeup of what I'm trying to do:

---

### Post by degan on 2009-11-22
I have installed KK..
Now this is conky:



```
deegan@deegan-karmic:~$ conky -Version
Conky 1.7.2 compiled Fri Oct 23 15:55:48 UTC 2009 for Linux 2.6.24-23-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2
deegan@deegan-karmic:~$
```

If I launch the conky in.lua with:
cpu0 cpu1 battery_percent memperc fs_used_perc
OK..
But if:



```

{
	name='wireless_link_qual_perc',
	arg='wlan0',
	max=100,
	bg_colour=0x3399cc,
	bg_alpha=0.2,
	fg_colour=0x3399cc,
	fg_alpha=0.6,
	x=350, y=100,
	radius=25,
	thickness=5,
	start_angle=-90,
	end_angle=180
    },
    {
	name='upspeedf',
	arg='wlan0',
	max=100,
	bg_colour=0x3399cc,
	bg_alpha=0.2,
	fg_colour=0x3399cc,
	fg_alpha=0.3,
	x=350, y=100,
	radius=15,
	thickness=4,
	start_angle=-90,
	end_angle=180
    },
    {
	name='downspeedf',
	arg='wlan0',
	max=100,
	bg_colour=0x3399cc,
	bg_alpha=0.2,
	fg_colour=0x3399cc,
	fg_alpha=0.3,
	x=350, y=100,
	radius=20,
	thickness=4,
	start_angle=-90,
	end_angle=180
     },
     {
	name='fs_used_perc',
	arg='/media/Xp black',
	max=100,
	bg_colour=0x3399cc,
	bg_alpha=0.2,
	fg_colour=0x3399cc,
	fg_alpha=0.3,
	x=900, y=40,
	radius=20,
	thickness=4,
	start_angle=-90,
	end_angle=180
	},
	{
	name='fs_used_perc',
	arg='/media/Xp black',
	max=100,
	bg_colour=0x3399cc,
	bg_alpha=0.2,
	fg_colour=0x3399cc,
	fg_alpha=0.2,
	x=900, y=40,
	radius=15,
	thickness=4,
	start_angle=-90,
	end_angle=180
	},
```



```
deegan@deegan-karmic:~$ conky -c .conkyrc3
Conky: desktop window (20000bc) is subwindow of root window (109)
Conky: window type - override
Conky: drawing to created window (0x4e00001)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_clock_rings execution failed: /home/deegan/Scrivania/clock_rings.lua:314: attempt to perform arithmetic on local 'value' (a nil value)
Conky: llua_do_call: function conky_clock_rings execution failed: /home/deegan/Scrivania/clock_rings.lua:314: attempt to perform arithmetic on local 'value' (a nil value)
^CConky: received SIGINT or SIGTERM to terminate. bye!
deegan@deegan-karmic:~$


```

---

### Post by searchOne on 2009-11-24
Hi londonali1010,
i have a problem with the lua, this error:
Not BAT1 that no error!

```

[search@localhost ~]$ conky
Conky: desktop window (1e000ba) is subwindow of root window (13f)
Conky: window type - normal
Conky: drawing to created window (0x4400001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT1/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT1/state: No such file or directory
Conky: llua_do_call: function conky_widgets execution failed: /home/search/conky/lua/widgets/conky_widgets.lua:323: attempt to perform arithmetic on local 'mem_process' (a nil value)

```
the lua-widget:
```

--[[
Conky Widgets by londonali1010 (2009)

This script is meant to be a "shell" to hold a suite of widgets for use in Conky.

To configure:
+ Copy the widget's code block (will be framed by --(( WIDGET NAME )) and --(( END WIDGET NAME )), with "[" instead of "(") somewhere between "require 'cairo'" and "function conky_widgets()", ensuring not to paste into another widget's code block
+ To call the widget, add the following just before the last "end" of the entire script:
    cr = cairo_create(cs)
    NAME_OF_FUNCTION(cr, OPTIONS)
    cairo_destroy(cr)
+ Replace OPTIONS with the options for your widget (should be specified in the widget's code block) 

Call this script in Conky using the following before TEXT (assuming you save this script to ~/scripts/conky_widgets.lua):
    lua_load ~/scripts/conky_widgets.lua
    lua_draw_hook_pre widgets
    
Changelog:
+ v1.0 -- Original release (17.10.2009)
]]

require 'cairo'

--[[ AIR CLOCK WIDGET ]]
--[[ Options (xc, yc, size):
    "xc" and "yc" are the x and y coordinates of the centre of the clock, in pixels, relative to the top left of the Conky window
    "size" is the total size of the widget, in pixels ]]

function air_clock(cr, xc, yc, size)
    local offset = 0
    
    shadow_width = size * 0.03
    shadow_xoffset = 0
    shadow_yoffset = size * 0.01
    
    if shadow_xoffset >= shadow_yoffset then
        offset = shadow_xoffset
    else offset = shadow_yoffset
    end
    
    local clock_r = (size - 2 * offset) / (2 * 1.25)
        
    show_seconds=true
    
    -- Grab time
    
    local hours=os.date("%I")
    local mins=os.date("%M")
    local secs=os.date("%S")
    
    secs_arc=(2*math.pi/60)*secs
    mins_arc=(2*math.pi/60)*mins
    hours_arc=(2*math.pi/12)*hours+mins_arc/12
    
    -- Drop shadow
    
    local ds_pat=cairo_pattern_create_radial(xc+shadow_xoffset,yc+shadow_yoffset,clock_r*1.25,xc+shadow_xoffset,yc+shadow_yoffset,clock_r*1.25+shadow_width)
    cairo_pattern_add_color_stop_rgba(ds_pat,0,0,0,0,0)  -- ,0,0,0,0.2
    cairo_pattern_add_color_stop_rgba(ds_pat,0,0,0,0,0) -- ,1,0,0,0,0
    
    cairo_move_to(cr,0,0)
    cairo_line_to(cr,conky_window.width,0)
    cairo_line_to(cr,conky_window.width, conky_window.height)
    cairo_line_to(cr,0,conky_window.height)
    cairo_close_path(cr)
    cairo_new_sub_path(cr)
    cairo_arc(cr,xc,yc,clock_r*1.25,0,2*math.pi)
    cairo_set_source(cr,ds_pat)
    cairo_set_fill_rule(cr,CAIRO_FILL_RULE_EVEN_ODD)
    cairo_fill(cr)
    
    -- Glassy border
    
    cairo_arc(cr,xc,yc,clock_r*1.25,0,2*math.pi)
    cairo_set_source_rgba(cr,0,0,0,0) -- ,0.5,0.5,0.5,0.2
    cairo_set_line_width(cr,1)
    cairo_stroke(cr)
    
    local border_pat=cairo_pattern_create_linear(xc,yc-clock_r*1.25,xc,yc+clock_r*1.25)
    
    cairo_pattern_add_color_stop_rgba(border_pat,0,0,0,0,0) -- ,0,1,1,1,0.7
    cairo_pattern_add_color_stop_rgba(border_pat,0,0,0,0,0) -- ,0.3,1,1,1,0
    cairo_pattern_add_color_stop_rgba(border_pat,0,0,0,0,0) -- ,0.5,1,1,1,0
    cairo_pattern_add_color_stop_rgba(border_pat,0,0,0,0,0) -- ,0.7,1,1,1,0
    cairo_pattern_add_color_stop_rgba(border_pat,0,0,0,0,0) -- ,1,1,1,1,0.7
    cairo_set_source(cr,border_pat)
    cairo_arc(cr,xc,yc,clock_r*1.125,0,2*math.pi)
    cairo_close_path(cr)
    cairo_set_line_width(cr,clock_r*0.25)
    cairo_stroke(cr)
    
    -- Set clock face
    
    cairo_arc(cr,xc,yc,clock_r,0,2*math.pi)
    cairo_close_path(cr)
    
    local face_pat=cairo_pattern_create_radial(xc,yc-clock_r*0.75,0,xc,yc,clock_r)
    
    cairo_pattern_add_color_stop_rgba(face_pat,0,0,0,0,0)        -- ,0,1,1,1,0.9
    cairo_pattern_add_color_stop_rgba(face_pat,0,0,0,0,0)      -- ,0.5,1,1,1,0.9
    cairo_pattern_add_color_stop_rgba(face_pat,0,0,0,0,0)  -- ,1,0.9,0.9,0.9,0.9
    cairo_set_source(cr,face_pat)
    cairo_fill_preserve(cr)
    cairo_set_source_rgba(cr,0,0,0,0) -- ,0.5,0.5,0.5,0.2
    cairo_set_line_width(cr, 1)
    cairo_stroke (cr)
    
    -- Draw hour hand
    
    xh=xc+0.7*clock_r*math.sin(hours_arc)
    yh=yc-0.7*clock_r*math.cos(hours_arc)
    cairo_move_to(cr,xc,yc)
    cairo_line_to(cr,xh,yh)
    
    cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
    cairo_set_line_width(cr,5)
    cairo_set_source_rgba(cr,0,0,0,0.8) -- ,0,0,0,0.4
    cairo_stroke(cr)
    
    -- Draw minute hand
    
    xm=xc+0.9*clock_r*math.sin(mins_arc)
    ym=yc-0.9*clock_r*math.cos(mins_arc)
    cairo_move_to(cr,xc,yc)
    cairo_line_to(cr,xm,ym)
    
    cairo_set_line_width(cr,3)
    cairo_stroke(cr)
    
    -- Draw seconds hand
    
    if show_seconds then
        xs=xc+0.9*clock_r*math.sin(secs_arc)
        ys=yc-0.9*clock_r*math.cos(secs_arc)
        cairo_move_to(cr,xc,yc)
        cairo_line_to(cr,xs,ys)
    
        cairo_set_line_width(cr,1)
        cairo_stroke(cr)
    end
end

--[[ END AIR CLOCK WIDGET ]]

--[[ RING WIDGET ]]
--[[ Options (name, arg, max, bg_colour, bg_alpha, xc, yc, radius, thickness, start_angle, end_angle):
    "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
    "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
    "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
    "bg_colour" is the colour of the base ring.
    "bg_alpha" is the alpha value of the base ring.
    "fg_colour" is the colour of the indicator part of the ring.
    "fg_alpha" is the alpha value of the indicator part of the ring.
    "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
    "radius" is the radius of the ring.
    "thickness" is the thickness of the ring, centred around the radius.
    "start_angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
    "end_angle" is the ending angle of the ring, in degrees, clockwise from top. Value can be either positive or negative, but must be larger (e.g. more clockwise) than start_angle. ]]

function ring(cr, name, arg, max, bgc, bga, fgc, fga, xc, yc, r, t, sa, ea)
    local function rgb_to_r_g_b(colour,alpha)
        return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
    end
    
    local function draw_ring(pct)
        local angle_0=sa*(2*math.pi/360)-math.pi/2
        local angle_f=ea*(2*math.pi/360)-math.pi/2
        local pct_arc=pct*(angle_f-angle_0)

        -- Draw background ring

        cairo_arc(cr,xc,yc,r,angle_0,angle_f)
        cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
        cairo_set_line_width(cr,t)
        cairo_stroke(cr)
    
        -- Draw indicator ring

        cairo_arc(cr,xc,yc,r,angle_0,angle_0+pct_arc)
        cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
        cairo_stroke(cr)
    end
    
    local function setup_ring()
        local str = ''
        local value = 0
        
        str = string.format('${%s %s}', name, arg)
        str = conky_parse(str)
        
        value = tonumber(str)
        if value == nil then value = 0 end
        pct = value/max
        
        draw_ring(pct)
    end    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then setup_ring() end
end

--[[ END RING WIDGET ]]

--[[ GRADIENT RING WIDGET ]]
--[[ Options (name, arg, max, colour, alpha, x, y, inner_radius, outer_radius, frac, thickness, start_angle, end_angle):
        "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
        "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
        "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
        "fg_colour" is the colour of the ring.
        "fg_alpha" is the alpha value of the ring.
        "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
        "inner_radius" is the inner radius of the ring.
        "outer_radius" is the outer radius of the ring.  
        "frac" determines the extent of the gradient around the ring - 2 implies the gradient fades halfway around the ring, 4 equals a quarter of the way, etc...      
        "thickness" is the thickness of the ring, centred around the radius.
        "start_angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
        "end_angle" is the ending angle of the ring, in degrees, clockwise from top. Value can be either positive or negative, but must be larger (e.g. more clockwise) than start_angle. ]]
     
function gradient_ring(cr, name, arg, max, fgc, fga, xc, yc, ring_i, ring_o, frac, t, sa, ea)
        local function rgb_to_r_g_b(colour,alpha)
            return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
        end
     
        local function draw_gradient_ring(pct)
            local angle_0=sa*(2*math.pi/360)-math.pi/2
            local angle_f=ea*(2*math.pi/360)-math.pi/2
            local pct_arc=pct*(angle_f-angle_0)
     
            for i = 1,max/frac do
                cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga*i/max)) --for flat shading of bars
        
                --local pat=cairo_pattern_create_linear(xc-ring_i*math.sin(angle_0+t_arc+2*math.pi*i/max),yc+ring_i*math.cos(angle_0+t_arc+2*math.pi*i/max),xc-ring_o*math.sin(angle_0+t_arc+2*math.pi*i/max),yc+ring_o*math.cos(angle_0+t_arc+2*math.pi*i/max))
                --cairo_pattern_add_color_stop_rgba(pat,0,rgb_to_r_g_b(fgc,0))
                --cairo_pattern_add_color_stop_rgba(pat,1,rgb_to_r_g_b(fgc,fga*i/max))
                --cairo_set_source(cr,pat) -- for gradient shading of bars
        
                cairo_move_to(cr,xc-ring_i*math.cos(angle_0+pct_arc+2*math.pi*i/max),yc-ring_i*math.sin(angle_0+pct_arc+2*math.pi*i/max))
                cairo_line_to(cr,xc-ring_o*math.cos(angle_0+pct_arc+2*math.pi*i/max),yc-ring_o*math.sin(angle_0+pct_arc+2*math.pi*i/max))
    
                cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
                cairo_set_line_width(cr,t)
                cairo_stroke(cr)
            end
        end
     
        local function setup_gradient_ring()
            local str = ''
            local value = 0
     
            str = string.format('${%s %s}', name, arg)
            str = conky_parse(str)
     
            value = tonumber(str)
            if value == nil then value = 0 end
            pct = value/max
     
            draw_gradient_ring(pct)
        end    
     
        local updates=conky_parse('${updates}')
        update_num=tonumber(updates)
     
        if update_num>5 then setup_gradient_ring() end
    end
     
--[[ END GRADIENT RING WIDGET ]]

--[[ PIE WIDGET ]]
--[[ xc,yc - center of the pie
     r - radius of the pie ]]

function pie_rings (xc, yc, r)

    pat = cairo_pattern_create_radial (xc, yc, 0.2*r, xc,  yc, r);
    cairo_pattern_add_color_stop_rgba (pat, 0.1, 1, 1, 1, 0);
    cairo_pattern_add_color_stop_rgba (pat, 1.0, 1, 1, 1, 0.3);
    cairo_set_source (cr, pat);
    cairo_arc (cr, xc, yc, r, 0, 2 * math.pi);
    cairo_fill (cr);
    cairo_pattern_destroy (pat);


    cairo_set_font_size (cr, 10)
    cairo_select_font_face (cr, "LCDMono",
                CAIRO_FONT_SLANT_NORMAL,
                CAIRO_FONT_WEIGHT_NORMAL)    
    cairo_set_line_width (cr, 2.0)

    -- Show total mem usage
    local str1 = conky_parse(string.format('${mem}'))
    local str2 = string.match(str1, "(%d+)")
    local str3 = string.match(str1, "(%a+)")

    cairo_set_source_rgba(cr, 1, 1, 1, 1)
    cairo_move_to (cr, xc-9, yc-1)
    cairo_show_text (cr, str2)
    cairo_move_to (cr, xc-9, yc+9)
    cairo_show_text (cr, str3)
    cairo_stroke(cr)

    -- Get top mem usage
    local str1 = conky_parse(string.format('${mem}'))
    local mem = tonumber(string.match(str1, "(%d+)"))
    local str1 = conky_parse(string.format('${memperc}'))
    local mempct = tonumber(string.match(str1, "(%d+)"))
    
    -- Draw pie
    local angle = -90
    local angle2 = 0
    local tro = 4        -- Text rotational offset (degrees)
    local maxprocesses = 7
    local maxstrlen = 8

    for process = 1, maxprocesses do

        cairo_save(cr)
    
        -- Get top process memory usage
        local str2 = conky_parse(string.format('${top_mem mem %i}', tonumber(process)))
        local mem_process = tonumber(str2)
        local procpct = mem_process / mempct      <<<<<<<<<< this is Line 323
        angle2 = angle + (procpct*360)

        if angle2 > 260 then
            cairo_restore(cr)
            break
        end    

        -- Get top process name
        local str2 = conky_parse(string.format('${top_mem name %i} ', tonumber(process)))
        local index = string.find(str2,' ')
        
        if (index == nil) then
            cairo_restore(cr)
            break
        elseif (index > maxstrlen) then
            str2 = string.sub(str2, 0, maxstrlen)
        end

        -- Draw pie outline
        cairo_set_source_rgba(cr, 1, 1, 1, 0.2)        
        cairo_arc_negative (cr, xc, yc, 0.2*r, angle2*(math.pi/180), angle*(math.pi/180));            
        cairo_arc (cr, xc, yc, r, angle*(math.pi/180), angle2*(math.pi/180));    
--        cairo_close_path(cr)
        cairo_stroke(cr)

        -- Draw text
        cairo_set_source_rgba(cr, 1, 1, 1, 1)    
        cairo_move_to(cr, xc, yc)
        cairo_rotate(cr, (angle2-((angle2-angle)/2)+tro)*(math.pi/180))
--        cairo_show_text (cr, '    '..(procpct*100))
        if (index > maxstrlen) then
            cairo_show_text (cr, '      '..str2..'..')
        else
            cairo_show_text (cr, '      '..str2)
        end        

        angle = angle2 + 3

        cairo_stroke(cr)
        cairo_restore(cr)
    end

    if (angle < 264) then
        angle2 = 267
        cairo_set_source_rgba(cr, 1, 1, 1, 0.2)    
        cairo_arc_negative (cr, xc, yc, 0.2*r, angle2*(math.pi/180), angle*(math.pi/180));
        cairo_arc (cr, xc, yc, r, angle*(math.pi/180), angle2*(math.pi/180));    
--        cairo_close_path(cr)
        cairo_stroke(cr)
        
        if ((angle2 - angle) > 20) then
            cairo_set_source_rgba(cr, 1, 1, 1, 0.5)    
            cairo_move_to(cr, xc, yc)
            cairo_rotate(cr, (angle2-((angle2-angle)/2)+tro+2)*(math.pi/180))
            cairo_show_text (cr, '      '..'other')
            cairo_stroke(cr)
        end
    end
end
--[[ END PIE WIDGET ]]

function conky_widgets()
    if conky_window == nil then return end
    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    
    cr = cairo_create(cs)
    air_clock(cr, 90, 90, 200) -- options: xc, yc, size
    cairo_destroy(cr)
    
    cr = cairo_create(cs)
    ring(cr, 'time', '+%S', 60, 0xE3E3E3, 0, 0xFFFF00, 0.7, 90, 90, 70, 4, 0, 360) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)
    
    cr = cairo_create(cs)
    ring(cr, 'time', '+%M', 60, 0xE3E3E3, 0.1, 0x00CD00, 0.7, 90, 90, 64, 7, 0, 360) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)
    
    cr = cairo_create(cs)
    ring(cr, 'time', '+%H', 24, 0xE3E3E3, 0.2, 0xffffff, 0.7, 90, 90, 53, 14, 0, 360) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)
    
    cr = cairo_create(cs)
    ring(cr, 'battery_percent', 'BAT1', 100, 0xFF0000, 0.4, 0xFFFF00, 0, 90, 90, 80, 14, 0, 180) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)
    
    cr = cairo_create(cs)
    ring(cr, 'battery_percent', 'BAT1', 100, 0xFF0000, 0.8, 0xFFFF00, 0, 90, 90, 75, 4, 180, 360) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)
    
    cr = cairo_create(cs)
    ring(cr, 'battery_percent', 'BAT1', 100, 0xFF0000, 0.8, 0xFFFF00, 0, 90, 90, 86, 2, 180, 360) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)

    cr = cairo_create(cs)
    ring(cr, 'cpu', 'CPU0', 100, 0xA1A1A1, 0.4, 0xFFFF00, 1, 90, 590, 86, 12, 0, 270) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)
    
    cr = cairo_create(cs)
    ring(cr, 'cpu', 'CPU1', 100, 0xA1A1A1, 0.4, 0xCDCD00, 1, 90, 590, 73, 12, 0, 270) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)

    cr = cairo_create(cs)
    ring(cr, 'memperc', '', 100, 0xA1A1A1, 0.4, 0x708090, 1, 90, 590, 60, 12, 0, 270) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)

    cr = cairo_create(cs)
    ring(cr, 'battery_percent', 'BAT0', 100, 0xA1A1A1, 0.4, 0xFF8C00, 1, 90, 590, 47, 12, 0, 270) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)

    cr = cairo_create(cs)
    ring(cr, 'fs_used_perc', '/', 100, 0xA1A1A1, 0.4, 0x008B00, 1, 90, 590, 34, 12, 0, 270) -- options: name, arg, max, bg_colour, bg_alpha, fg_colour, fg_alpha, xc, yc, radius, thickness, start_angle, end_angle
    cairo_destroy(cr)

    cr = cairo_create(cs)
    local w = conky_window.width
    local h = conky_window.height

    r = 75
    xc = 90
    yc = 360
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        pie_rings(xc, yc, r)
    end

        cairo_destroy(cr)

end

```Have you Idea? :p

---

### Post by londonali1010 on 2009-11-24
^^^ mem_process isn't an actual variable...Did you mean to write mem_percent?

---

### Post by searchOne on 2009-11-24
oh is it not a mistake?
```
Conky: llua_do_call: function conky_widgets execution failed: /home/search/conky/lua/widgets/conky_widgets.lua:323: attempt to perform arithmetic on local 'mem_process' (a nil value)
```

---

### Post by londonali1010 on 2009-11-24
> **searchOne said:**
> oh is it not a mistake?
```
Conky: llua_do_call: function conky_widgets execution failed: /home/search/conky/lua/widgets/conky_widgets.lua:323: attempt to perform arithmetic on local 'mem_process' (a nil value)
```

Oh! I didn't see the pie widget in there.  D'oh!

Well, I haven't run that widget myself, but at first glance, it looks like mem_process is returning a nil value (sorry, that's probably obvious).  You can error-check it by inserting a line that says:
```
if mem_process == nil then mem_process = 0 end
```
That will at least keep you from getting the error message. But it may still mean that if there's another problem, it will always display zero.  Try it and see if that helps.

---

### Post by searchOne on 2009-11-25
> **londonali1010 said:**
> Oh! I didn't see the pie widget in there.  D'oh!

Well, I haven't run that widget myself, but at first glance, it looks like mem_process is returning a nil value (sorry, that's probably obvious).  You can error-check it by inserting a line that says:
```
if mem_process == nil then mem_process = 0 end
```That will at least keep you from getting the error message. But it may still mean that if there's another problem, it will always display zero.  Try it and see if that helps.

 Hi londonali1010, Thanks for your help, but where am I supposed to use the line in the widget?

---

### Post by londonali1010 on 2009-11-25
> **searchOne said:**
> Hi londonali1010, Thanks for your help, but where am I supposed to use the line in the widget?

Oh, sorry. Just pop it in directly above your current line 323. It just does a quick error check on the mem_process value before proceeding.

---

### Post by searchOne on 2009-11-25
Hi londonali1010,

as always just the right help!
It now runs without error, absolutely correct. :D

Thank you. :KS

CHIMO!
Stefan

---

### Post by condor216 on 2009-12-08
```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
update_interval .5
no_buffers yes
uppercase no
color1 F8DF58
minimum_size 400 1000
gap_x 5
gap_y 0
temperature_unit fahrenheit
border_inner_margin
lua_load /home/gee/scripts/lua.lua

TEXT
${voffset 30}${color white}${font OpenLogos:size=22}u${color}${font size=12}SYSTEM ${hr 4}
        ${offset -6}${font StyleBats:size=16}q${font} Uptime: ${alignr}${uptime}
        ${font Weather:size=16}xyz${font} CPU Temp: ${alignr}${acpitemp}°F
        ${font StyleBats:size=16}A${font} CPU1: ${cpu cpu1}% ${alignr}${cpugraph cpu1 15,120 000000 ffffff -t -l}
        ${voffset -15}${font StyleBats:size=16}A${font} CPU2: ${cpu cpu2}% ${alignr}${cpugraph cpu2 15,120 000000 ffffff -t -l}
        ${voffset -15}${font StyleBats:size=16}g${font} RAM: $memperc% ${alignr}${membar 15,120}
        ${if_existing /sys/class/power_supply/BAT0}${voffset -17}${font Webdings:size=16}~${font} Battery: ${alignr}${battery_bar 15,120 BAT0}
                             ${voffset -12}${font StyleBats:size=16}x${font}${battery}            ${alignr 30}${battery_time}${else}${voffset -20}${endif}
    ${offset 7}${font StyleBats:size=16}A${font} HIGHEST CPU${voffset -8}${alignr 27}${font StyleBats:size=16}g${font} HIGHEST MEM
 ${goto 40}${top name 1}${alignc 120}${top cpu 1}        ${alignr 2}${top_mem name 1}${alignr}${top_mem mem 1}
${voffset }
${color white}${voffset -18}${font StyleBats:size=22}p${color}${font size=12}DISK I/O ${hr 2}${font}
        ${offset 25}${font StyleBats:size=16}h${font}Read: ${diskio_read } ${alignr}${diskiograph_read /dev/sda 15,120 000000 0000FF 2}
        ${offset 25}${voffset -15}${font StyleBats:size=16}f${font}Write: ${diskio_write } ${alignr}${diskiograph_write /dev/sda 15,120 000000 FF0000 2}
${color white}${voffset -25}${font StyleBats:size=22}c${color}${font size=12}NETWORK ${hr 2}
    ${font StyleBats:size=16}v${font}External IP: ${alignr}${execi 3600 wget -O - http://ip.tupeux.com | tail}
${if_existing /proc/net/route eth0}
    ${voffset -15}${font StyleBats:size=16}0${font size=18} Wired${font}
                    ${font StyleBats:size=16}r${font}Up: ${upspeed eth0} k/s ${alignr}${upspeedgraph eth0 15,100 000000 F80300 -t -l}
                    ${voffset -15}${font StyleBats:size=16}t${font}Down: ${downspeed eth0}k/s ${alignr}${downspeedgraph eth0 15,100 000000 00F83D -t -l}
                    ${voffset -10}${font PizzaDude Bullets:size=14}a${font} Local Ip: ${alignr}${addr eth0}${endif}
${if_existing /proc/net/route wlan0}
      ${voffset -15}${font StyleBats:size=16}l${font size=18}Wireless${font}
                    ${font stylebats:size=14}u${font}access point:${alignr}${wireless_essid wlan0}
                    ${font StyleBats:size=14}r${font}Up: ${color }${upspeed wlan0} k/s ${alignr}${upspeedgraph wlan0 15,100  000000 F80300 -t -l}
                    ${voffset -15}${font StyleBats:size=16}t${font}Down: ${color }${downspeed wlan0}k/s ${alignr}${downspeedgraph wlan0 15,100 000000 00F83D -t -l}
                    ${voffset -8}${font stylebats:size=14}k${font} wireless quality:${wireless_link_qual_perc wlan0}%${alignr}${voffset -5}${wireless_link_bar 15,100 wlan0}${voffset -15}
                    ${voffset 4}${font PizzaDude Bullets:size=14}a${font} Local Ip: ${alignr}${addr wlan0}
                    ${voffset 1}${font stylebats:size=14}z${font} wireless MAC adress: ${alignr}${wireless_ap wlan0}        
${else}${voffset -20}
${endif}

${font DejaVu Sans:size=40}${alignr}${lua_parse datey 51.045 -114.057222 1.5}${time %k:%M}${color}
${font}Name               PID   CPU%   MEM%
${conky_parse top_cpu_colour 1}
${lua_parse top_cpu_colour 2}
${lua_parse top_cpu_colour 3}
${lua_parse top_cpu_colour 4}
${color}Mem usage
${lua_parse top_mem_colour 1}
${lua_parse top_mem_colour 2}
${components_to_colour(11,12,13)

${hr 1}
``````
--
-- Conky Lua scripting example
--
-- Copyright (c) 2009 Brenden Matthews, all rights reserved.
--
-- This program is free software: you can redistribute it and/or modify
-- it under the terms of the GNU General Public License as published by
-- the Free Software Foundation, either version 3 of the License, or
-- (at your option) any later version.
--

function components_to_colour(r, g, b)
    -- Take the RGB components r, g, b, and return an RGB integer
    return ((math.floor(r + 0.5) * 0x10000) + (math.floor(g + 0.5) * 0x100) + math.floor(b + 0.5)) % 0xffffff -- no bit shifting operator in Lua afaik
end

function colour_to_components(colour)
    -- Take the RGB components r, g, b, and return an RGB integer
    return (colour / 0x10000) % 0x100, (colour / 0x100) % 0x100, colour % 0x100
end

function conky_top_colour(value, default_colour, lower_thresh, upper_thresh)
    --[[
    This function returns a colour based on a threshold, by adding more of
    the red component and reducing the other components.  ``value'' is the
    value we're checking the thresholds against, ``default_colour'' is the
    original colour (before adjusting), and the ``lower_thresh'' and
    ``upper_thresh'' parameters are the low and high values for which we
    start applying redness.
    ]]
    local r, g, b = colour_to_components(default_colour)
    local colour = 0
    if value ~= nil and (value - lower_thresh) > 0 then
        if value > upper_thresh then value = upper_thresh end
        local perc = (value - lower_thresh) / (upper_thresh - lower_thresh)
        if perc > 1 then perc = 1 end
        -- add some redness, depending on where ``value'' lies within the
        -- threshhold range
        r = r + perc * (0xff - r)
        b = b - perc * b
        g = g - perc * g
    end
    colour = components_to_colour(r, g, b)

    return string.format("${color #%06x}", colour)
end

-- parses the output from top and calls the colour function
function conky_top_cpu_colour(arg)
    -- input is the top var number we want to use
    local str = conky_parse(string.format(' ${top name %i} ${top pid %i} ${top cpu %i} ${top mem %i}', tonumber(arg), tonumber(arg), tonumber(arg), tonumber(arg)))
    local cpu = tonumber(string.match(str, '(%d+%.%d+)'))
    -- tweak the last 3 parameters to your liking
    -- my machine has 4 CPUs, so an upper thresh of 25% is appropriate
    return conky_top_colour(cpu, 0xd3d3d3, 15, 25) .. str
end

function conky_top_mem_colour(arg)
    -- input is the top var number we want to use
    local str = conky_parse(string.format(' ${top_mem name %i} ${top_mem pid %i} ${top_mem cpu %i} ${top_mem mem %i}', tonumber(arg), tonumber(arg), tonumber(arg), tonumber(arg)))
    local mem = tonumber(string.match(str, '%d+%.%d+%s+(%d+%.%d+)'))
    -- tweak the last 3 parameters to your liking
    -- my machine has ~8GiB of ram, so an upper thresh of 15% seemed appropriate
    return conky_top_colour(mem, 0xd3d3d3, 5, 15) .. str
end

function colour_transition(start, stop, position)
    --[[
    Transition from one colour to another based on the value of
    ``position'', which should be a number between 0 and 1.
    ]]
    local rs, gs, bs = colour_to_components(start) -- start components
    local re, ge, be = colour_to_components(stop) -- end components
    local function tr(s, e, p)
        return e + (e - s) * p
    end
    local rr, gr, br = tr(rs, re, position), tr(gs, ge, position), tr(bs, be, position) -- result components
    return components_to_colour(rr, gr, br)
end
```

those are my sysmon conky and .lua script respectivly does any1 see any problems why the lua funtions would return nil?

please linux man HELP!

---

### Post by 5BallJuggler on 2009-12-08
As I am expecting to be a dad soon, I thought it would be nice to have a photo album on my desktop, I'm using Londonali's script, 

I get this error
```

Conky: llua_do_call: function conky_photo_album execution failed: attempt to call a nil value
```

here is the script

```
--[[
Photo Album by londonali1010 (2009)

This script draws a photo album of the files in a specified directory.  Files will be displayed in order; there is currently no option to randomise.

To call this script in Conky (assuming that you have saved it as ~/scripts/photo_album.lua), use the following before TEXT:
    lua_load ~/scripts/photo_album.lua
    lua_draw_hook_pre photo_album
    
Changelog:
+ v1.0 -- Original release (03.11.2009)
]]

require 'cairo'
require 'imlib2'

-- OPTIONS
-- "album_dir" is the directory containing the images for your photo album; please note that the path must be absolute (e.g. no "~")
album_dir = "/home/phil/Documents/MyPictures/"
-- "xc" and "yc" are the coordinates of the centre of the photo album, relative to the top left corner of the Conky window, in pixels
xc, yc = 150, 120
-- "w_max" and "h_max" are the maximum dimensions, in pixels, that you want the widget to be.  The script will ensure that the photo album fits inside the box bounded by w_max and h_max
w_max, h_max = 300, 240
-- "t" is the thickness of the frame, in pixels
t = 6
-- "update_interval" is the number of Conky updates between refreshes
update_interval = 1

function get_file_to_use()
    num_files = tonumber(conky_parse("${exec ls -A " .. album_dir .. " | wc -l}"))
    if num_files == nil then num_files = 0 end
    if num_files == 0 then return "none" end
    
    updates = tonumber(conky_parse("${updates}"))
    whole = math.ceil(updates/update_interval)
    
    if whole <= num_files
    then
        num_file_to_show = whole
    else
        whole = whole % num_files
        num_file_to_show = whole
    end
    
    return conky_parse("${exec ls " .. album_dir .. " | sed -n " .. num_file_to_show .. "p}")
end

function init_drawing_surface()
    imlib_set_cache_size(4096 * 1024)
    imlib_context_set_dither(1)
end

function draw_frame()
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual,  conky_window.width, conky_window.height)
    
    cr = cairo_create(cs)
    
    cairo_rectangle(cr, xc - width/2 - t, yc - height/2 - t, width + 2*t, height + 2*t)
    cairo_set_source_rgba(cr, 1, 1, 1, 0.8)
    cairo_fill(cr)   
    
    cairo_destroy(cr)
end

function draw_image()
    init_drawing_surface()
    
    image = imlib_load_image(album_dir .. filename)
    if image == nil then return end
    imlib_context_set_image(image)
	
	w_img, h_img = imlib_image_get_width(), imlib_image_get_height()
	if w_img >= h_img
	then
	    width = w_max - 2*t
	    height = width * (h_img/w_img)
	else
	    height = h_max - 2*t
	    width = height * (w_img/h_img)
	end
	
	draw_frame()
	
	buffer = imlib_create_image(width, height)
	imlib_context_set_image(buffer)
	
	imlib_blend_image_onto_image(image, 0, 0, 0, w_img, h_img, 0, 0, width, height)
	imlib_context_set_image(image)
	imlib_free_image()
	
	imlib_context_set_image(buffer)
	imlib_render_image_on_drawable(xc - width/2, yc - height/2)
	imlib_free_image()
end


function conky_photo_album()
    if conky_window == nil then return end
    filename = get_file_to_use()
    if filename == "none"
    then
        print( .. album_dir .. ": No files found")
    else
        draw_image()
    end
end

```

I'm calling it as suggested, but I can't make it work.

Can anyone help please..

Phil

---

### Post by Jefferythewind on 2009-12-08
Those circles are hot!

---

### Post by londonali1010 on 2009-12-09
> **5BallJuggler said:**
> As I am expecting to be a dad soon, I thought it would be nice to have a photo album on my desktop, I'm using Londonali's script, 

I get this error
```

Conky: llua_do_call: function conky_photo_album execution failed: attempt to call a nil value
```

here is the script

*snip*

I'm calling it as suggested, but I can't make it work.

Can anyone help please..

Phil

Probably seems obvious, but can you post your .conkyrc?

Also, where have you saved your script, and I assume that you are using 1.7.2 with Cairo and imlib2 bindings?

---

### Post by 5BallJuggler on 2009-12-09
> **londonali1010 said:**
> Probably seems obvious, but can you post your .conkyrc?

Also, where have you saved your script, and I assume that you are using 1.7.2 with Cairo and imlib2 bindings?

As requested, 

```
conky -v
Conky 1.7.2 compiled Fri Oct 23 15:55:48 UTC 2009 for Linux 2.6.24-23-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

```

```
# -- Conky settings -- #
background no
update_interval 30

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 300 230
maximum_width 300

alignment bottom_right
gap_x 20
gap_y 20

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# -- Text settings -- #
use_xft yes
xftfont London Between:size=10
xftalpha 0.8

uppercase no

default_color FFFFFF

# -- Lua Load -- #
lua_load ~/scripts/photo_album.lua
lua_draw_hook_pre photo_album

TEXT
 
```

---

### Post by 5BallJuggler on 2009-12-10
> **5BallJuggler said:**
> As I am expecting to be a dad soon, I thought it would be nice to have a photo album on my desktop, I'm using Londonali's script, 

I get this error
```

Conky: llua_do_call: function conky_photo_album execution failed: attempt to call a nil value
```

I'm calling it as suggested, but I can't make it work.

Can anyone help please..

Phil

@Londonali. Don't Panic!!!

I've fixed, but feel a bit of a berk.

I had saved the correct photo_album.lua in the wrong place, and a "Wrong" photo_album in the right place, it turns out that in the command -
```
if whole <= num_files
```
cannot run like this -
```
if whole < = num_files
```

and that was the only error that I had. 

It only took me 3 days to find it, and as it turns out the file that I posted on here was correct.

Aaaaargh!!!!!

Thanks for trying to help

---

### Post by londonali1010 on 2009-12-11
> **5BallJuggler said:**
> @Londonali. Don't Panic!!!

I've fixed, but feel a bit of a berk.

I had saved the correct photo_album.lua in the wrong place, and a "Wrong" photo_album in the right place, it turns out that in the command -
```
if whole <= num_files
```
cannot run like this -
```
if whole < = num_files
```

and that was the only error that I had. 

It only took me 3 days to find it, and as it turns out the file that I posted on here was correct.

Aaaaargh!!!!!

Thanks for trying to help

Oh, good, it's true you had me a bit stumped :)  Anyway, don't feel bad, I do things like that quite regularly...:KS

---

### Post by 5BallJuggler on 2009-12-14
> **londonali1010 said:**
> Oh, good, it's true you had me a bit stumped :)  Anyway, don't feel bad, I do things like that quite regularly...:KS

Right, I know I said I fixed it, but I lied, when the album has displayed all of it's pictures, the place that should show the first picture again remains blank.
if i run conky from the terminal I get this error at the same time,
I think it is trying to display picture 0(ZERO) does anyone have any ideas how I can fix it?
```
sed: -e expression #1, char 2: invalid usage of line address 0
```

Here is the script
```
require 'cairo'
require 'imlib2'
 
-- OPTIONS
-- "album_dir" is the directory containing the images for your photo album; please note that the path must be absolute (e.g. no "~")
album_dir = "/home/phil/Documents/MyPictures/"
-- "xc" and "yc" are the coordinates of the centre of the photo album, relative to the top left corner of the Conky window, in pixels
xc, yc = 140, 140
-- "w_max" and "h_max" are the maximum dimensions, in pixels, that you want the widget to be.  The script will ensure that the photo album fits inside the box bounded by w_max and h_max
w_max, h_max = 280, 140
-- "t" is the thickness of the frame, in pixels
t = 2
-- "update_interval" is the number of Conky updates between refreshes
update_interval = 1
 
function get_file_to_use()
    num_files = tonumber(conky_parse("${exec ls -A " .. album_dir .. " | wc -l}"))
    if num_files == nil then num_files = 0 end
    if num_files == 0 then return "none" end
 
    updates = tonumber(conky_parse("${updates}"))
    whole = math.ceil(updates/update_interval)
 
    if whole <= num_files
    then
        num_file_to_show = whole
    else
        whole = whole % num_files
        num_file_to_show = whole
    end
 
    return conky_parse("${exec ls " .. album_dir .. " | sed -n " .. num_file_to_show .. "p}")
end
 
function init_drawing_surface()
    imlib_set_cache_size(4096 * 1024)
    imlib_context_set_dither(1)
end
 
function draw_frame()
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual,  conky_window.width, conky_window.height)
 
    cr = cairo_create(cs)
 
    cairo_rectangle(cr, xc - width/2 - t, yc - height/2 - t, width + 2*t, height + 2*t)
    cairo_set_source_rgba(cr, 0.1, 0.4, 1, 0.4)
    cairo_fill(cr)   
 
    cairo_destroy(cr)
end
 
function draw_image()
    init_drawing_surface()
 
    image = imlib_load_image(album_dir .. filename)
    if image == nil then return end
    imlib_context_set_image(image)
 
	w_img, h_img = imlib_image_get_width(), imlib_image_get_height()
	if w_img >= h_img
	then
	    width = w_max - 2*t
	    height = width * (h_img/w_img)
	else
	    height = h_max - 2*t
	    width = height * (w_img/h_img)
	end
 
	draw_frame()
 
	buffer = imlib_create_image(width, height)
	imlib_context_set_image(buffer)
 
	imlib_blend_image_onto_image(image, 0, 0, 0, w_img, h_img, 0, 0, width, height)
	imlib_context_set_image(image)
	imlib_free_image()
 
	imlib_context_set_image(buffer)
	imlib_render_image_on_drawable(xc - width/2, yc - height/2)
	imlib_free_image()
end
 
 
function conky_photo_album()
    if conky_window == nil then return end
    filename = get_file_to_use()
    if filename == "none"
    then
        print(album_dir .. ": No files found")
    else
        draw_image()
    end
end
```
Thanks in Advance 
Phil

ps it doesn't display the last picture either, the work around is put a picture I don't want to display and call it zzzzzzzz.jpg

---

### Post by londonali1010 on 2009-12-14
Hi Phil...if you put the following in your terminal prompt, can you confirm that it outputs the correct number of files in the album_dir?
```
ls -A <album_dir> | wc -l
```

---

### Post by 5BallJuggler on 2009-12-14
> **londonali1010 said:**
> Hi Phil...if you put the following in your terminal prompt, can you confirm that it outputs the correct number of files in the album_dir?
```
ls -A <album_dir> | wc -l
```

```
phil@phil-netbook:~$ exec ls -A "/home/phil/Documents/MyPictures/" | wc -l
16
```
```
phil@phil-netbook:~$ exec ls "/home/phil/Documents/MyPictures" | sed -n p
10.jpg
11.jpg
12.jpg
13.bmp
14.jpg
15.jpg
1.jpg
2.jpg
3.jpg
4.jpg
5.jpg
6.jpg
7.jpg
8.jpg
9.jpg
zzzzzzzzzz.jpg
```

so the commands are returning the correct data.

---

### Post by londonali1010 on 2009-12-14
Well, your code matches mine and your album directory looks fine, so my next step would be to add some checks in the code and watch it run in the terminal...If you add in
```
print(updates, update_interval, num_file_to_show)
localfilename = conky_parse("${exec ls " .. album_dir .. " | sed -n " .. num_file_to_show .. "p}")
print(localfilename)
```
just before the "return", that should print, for every iteration of Conky, what update number you're on, the update interval, which file to show, and the name of the file it's returning. That should pinpoint where it's going wrong.

---

### Post by 5BallJuggler on 2009-12-14
> **londonali1010 said:**
> Well, your code matches mine and your album directory looks fine, so my next step would be to add some checks in the code and watch it run in the terminal...If you add in
```
print(updates, update_interval, num_file_to_show)
localfilename = conky_parse("${exec ls " .. album_dir .. " | sed -n " .. num_file_to_show .. "p}")
print(localfilename)
```
just before the "return", that should print, for every iteration of Conky, what update number you're on, the update interval, which file to show, and the name of the file it's returning. That should pinpoint where it's going wrong.

```
1	1	1
10.jpg
1	1	1
10.jpg
1	1	1
10.jpg
2	1	2
11.jpg
3	1	3
12.jpg
4	1	4
13.bmp
5	1	5
14.jpg
6	1	6
15.jpg
7	1	7
1.jpg
8	1	8
2.jpg
9	1	9
3.jpg
10	1	10
4.jpg
11	1	11
5.jpg
12	1	12
6.jpg
13	1	13
7.jpg
14	1	14
8.jpg
15	1	15
9.jpg
[COLOR="Red"][B]16	1	16
zzzzzzzzzz.jpg[/B][/COLOR]
17	1	1
10.jpg
18	1	2
11.jpg
19	1	3
12.jpg
20	1	4
13.bmp
21	1	5
14.jpg
22	1	6
15.jpg
23	1	7
1.jpg
24	1	8
2.jpg
25	1	9
3.jpg
26	1	10
4.jpg
27	1	11
5.jpg
28	1	12
6.jpg
29	1	13
7.jpg
30	1	14
8.jpg
31	1	15
9.jpg
32	1	0
[COLOR="red"][B]sed: -e expression #1, char 2: invalid usage of line address 0

sed: -e expression #1, char 2: invalid usage of line address 0[/B][/COLOR]
33	1	1
10.jpg
34	1	2
11.jpg
35	1	3
12.jpg
36	1	4
13.bmp
37	1	5
14.jpg
38	1	6
15.jpg

```

it seems that during the first cycle all of the files are called OK, but in subsequent cycles it misses out zzzzzzz.jpg and tries to call image 0(zero)

---

### Post by londonali1010 on 2009-12-15
Ah, I see...the index isn't reinitialising correctly at the end.

Replace
```
if whole <= num_files
then
    num_file_to_show = whole
else
    whole = whole % num_files
    num_file_to_show = whole
end
```

with
```
if whole <= num_files
then
    num_file_to_show = whole
else
    whole = whole % num_files
**[COLOR="Red"]    if whole == 0 then whole = num_files end[/COLOR]**
    num_file_to_show = whole
end
```

or
```
if whole <= num_files
then
    num_file_to_show = whole
else
**[COLOR="Red"]    whole = (whole - 1) % num_files + 1[/COLOR]**
    num_file_to_show = whole
end
```

Both should work, not sure which one's more efficient!

---

### Post by 5BallJuggler on 2009-12-15
Thanks Londonali

I used this one

```
if whole <= num_files
then
    num_file_to_show = whole
else
    whole = whole % num_files
    if whole == 0 then whole = num_files end
    num_file_to_show = whole
end
```

It works a treat, solving both issues 

Thanks very much
Phil

---

### Post by scyn on 2009-12-30
Hi everyone,

I'm new to conky, and after some time spent trying to install it, it finally compiled and installed.
It however seems that whenever i want to draw circles using cairo_xlib_surface_create, it wont work.

I am currently using Milax configuration files ([http://www.milax.org/?p=287](http://www.milax.org/?p=287)), eventhough i also tested with some of londonali1010's nice widgets.

It would seem that the display, drawable and visual fields of the conky_window variable are nil..

The error output of conky is:
```

42sh$ conky -c ~/.conkyrc                                                                                                                                                                     | 13:55
Conky: desktop window (67) is root window
Conky: window type - desktop
Conky: drawing to created window (0x1e00001)
Conky: drawing to double buffer
table: 0x8d892c8
nil
nil
nil
2
2
Conky: llua_do_call: function conky_ring_stats execution failed: /home/scyn/rings.lua:254: attempt to call global 'cairo_xlib_surface_create' (a nil value)
table: 0x8d892c8
nil
nil
nil
1002
602
Conky: llua_do_call: function conky_ring_stats execution failed: /home/scyn/rings.lua:254: attempt to call global 'cairo_xlib_surface_create' (a nil value)
table: 0x8d892c8
nil
nil
nil
1002
602
Conky: llua_do_call: function conky_ring_stats execution failed: /home/scyn/rings.lua:254: attempt to call global 'cairo_xlib_surface_create' (a nil value)
table: 0x8d892c8
nil
nil
nil
1002
602
Conky: llua_do_call: function conky_ring_stats execution failed: /home/scyn/rings.lua:254: attempt to call global 'cairo_xlib_surface_create' (a nil value)
table: 0x8d892c8
nil
nil
nil
1002
602
Conky: llua_do_call: function conky_ring_stats execution failed: /home/scyn/rings.lua:254: attempt to call global 'cairo_xlib_surface_create' (a nil value)
^CConky: received SIGINT or SIGTERM to terminate. bye!

```The intermediate prints between errors are the fields of conky_window.

Here are my conkyrc and clock_rings
```

# -- Conky settings -- #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0

# -- Window specifications -- #

own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 1020 600
maximum_width 1000

alignment tm
gap_x 10
gap_y 0

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# -- Text settings -- #
use_xft yes
xftfont Santana:size=24
xftalpha 0.8

uppercase no

default_color FFFFFF

# -- Lua Load -- #
lua_load ~/rings.lua
lua_draw_hook_pre conky_ring_stats

TEXT
${voffset 35}${font Santana:size=50}${alignr}${time %H.%M}${font}
${goto 160}${hr 2}
${goto 250}${time %A, %d %B %Y}

``````

--[[
Ring Meters by londonali1010 (2009)

This script draws percentage meters as rings. It is fully customisable; all options are described in the script.

IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.

To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/rings-v1.2.lua
    lua_draw_hook_pre ring_stats
    
Changelog:
+ v1.2 -- Added option for the ending angle of the rings (07.10.2009)
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]

settings_table = {
    {
        -- Edit this table to customise your rings.
        -- You can create more rings simply by adding more elements to settings_table.
        -- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
        name='time',
        -- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
        arg='%I.%M',
        -- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
        max=12,
        -- "bg_colour" is the colour of the base ring.
        bg_colour=0xffffff,
        -- "bg_alpha" is the alpha value of the base ring.
        bg_alpha=0.1,
        -- "fg_colour" is the colour of the indicator part of the ring.
        fg_colour=0xffffff,
        -- "fg_alpha" is the alpha value of the indicator part of the ring.
        fg_alpha=0.2,
        -- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
        x=165, y=170,
        -- "radius" is the radius of the ring.
        radius=50,
        -- "thickness" is the thickness of the ring, centred around the radius.
        thickness=5,
        -- "start_angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
        start_angle=0,
        -- "end_angle" is the ending angle of the ring, in degrees, clockwise from top. Value can be either positive or negative, but must be larger (e.g. more clockwise) than start_angle.
        end_angle=360
    },
    {
        name='time',
        arg='%M.%S',
        max=60,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.4,
        x=165, y=170,
        radius=56,
        thickness=5,
        start_angle=0,
        end_angle=360
    },
    {
        name='time',
        arg='%S',
        max=60,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.6,
        x=165, y=170,
        radius=62,
        thickness=5,
        start_angle=0,
        end_angle=360
    },
    {
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0,
        fg_colour=0xffffff,
        fg_alpha=0.1,
        x=165, y=170,
        radius=70,
        thickness=5,
        start_angle=60,
        end_angle=120
    },
    {
        name='cpu',
        arg='cpu2',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0,
        fg_colour=0xffffff,
        fg_alpha=0.1,
        x=165, y=170,
        radius=76,
        thickness=5,
        start_angle=60,
        end_angle=120
    },
    {
        name='cpu',
        arg='cpu0',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.4,
        x=165, y=170,
        radius=84.5,
        thickness=8,
        start_angle=60,
        end_angle=120
    },
    {
        name='battery_percent',
        arg='BAT1',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.6,
        x=165, y=170,
        radius=72,
        thickness=11,
        start_angle=122,
        end_angle=210
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.8,
        x=165, y=170,
        radius=83.5,
        thickness=8,
        start_angle=122,
        end_angle=210
    },
    {
        name='time',
        arg='%d',
        max=31,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.8,
        x=165, y=170,
        radius=70,
        thickness=5,
        start_angle=212,
        end_angle=360
    },
    {
        name='time',
        arg='%m',
        max=12,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.8,
        x=165, y=170,
        radius=76,
        thickness=5,
        start_angle=212,
        end_angle=360
    },
    {
        name='fs_used_perc',
        arg='/',
        max=150,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xffffff,
        fg_alpha=0.3,
        x=165, y=170,
        radius=108.5,
        thickness=3,
        start_angle=-120,
        end_angle=240
    },
    {
        name='fs_used_perc',
        arg='/',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xffffff,
        fg_alpha=0.3,
        x=165, y=170,
        radius=135,
        thickness=50,
        start_angle=-120,
        end_angle=120
    },
}

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(cr,t,pt)
    local w,h=conky_window.width,conky_window.height
    
    local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

    local angle_0=sa*(2*math.pi/360)-math.pi/2
    local angle_f=ea*(2*math.pi/360)-math.pi/2
    local t_arc=t*(angle_f-angle_0)

    -- Draw background ring

    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
    
    -- Draw indicator ring

    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
end

function conky_ring_stats()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
        
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
        
        value=tonumber(str)
        pct=value/pt['max']
        
        draw_ring(cr,pct,pt)
    end

    if conky_window==nil then return end
    print (conky_window)
    print (conky_window.display)
    print (conky_window.drawable)
    print (conky_window.visual)
    print (conky_window.width)
    print (conky_window.height)
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    
    local cr=cairo_create(cs)    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
    end
end

```Thanks in advance, and apologies for my english
Happy conking,

--
Scyn

---

### Post by chinmaya_n on 2009-12-31
While i was trying to have the photo album thing i get this error:```
Conky: llua_do_call: function conky_widgets execution failed: ...e/chinmaya/.conkyscripts/conky_widgets_duplicate.lua:150: attempt to call global 'cairo_xlib_surface_create' (a nil value)
```
I can run that air clock! but this is giving problem! My .conkyrc```

background no

cpu_avg_samples 2
net_avg_samples 1
    
use_xft yes
xftfont Radio Space:size=45
uppercase no

xftalpha 0.1
update_interval 1.0
use_spacer none

total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
#own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes
no_buffers yes

gap_x 15
gap_y 30
  
draw_shades no
draw_outline no
draw_borders no
#draw_graph_borders no

default_color white
default_shade_color white
default_outline_color white
alignment top_right

minimum_size 600 80
maximum_width 600
  
#override_utf8_locale yes
#text_buffer_size 256

color1 5e97f6
color2 FFFFFF

#--lua load --#
lua_load ~/.conkyscripts/conky_widgets_duplicate.lua
lua_draw_hook_pre conky_widgets

### Now we start drawing ! ###

TEXT
${voffset -10}${alignr}${time %d %B %Y}

${voffset -90}${goto 15} ${font Sans Bold:size=17} ${alignc} ${color1}CPU ${color2}${cpu cpu1}${color1} RAM ${color2}$memperc ${color1} DOWN ${color2}${downspeed eth0} ${color1} UP ${color2}${upspeed eth0}
``` And my conky_widgets_duplicate.lua (i copied the code from your script!):```
--[[ PHOTO ALBUM WIDGET ]]
--[[ by londonali1010 (2009) ]]
--[[ Options (album_dir, xc, yc, w_max, h_max, t, update_interval)
    "album_dir" is the directory containing the images for your photo album; please note that the path must be absolute (e.g. no "~")
    "xc" and "yc" are the coordinates of the centre of the photo album, relative to the top left corner of the Conky window, in pixels
    "w_max" and "h_max" are the maximum dimensions, in pixels, that you want the widget to be.  The script will ensure that the photo album fits inside the box bounded by w_max and h_max
    "t" is the thickness of the frame, in pixels
    "update_interval" is the number of Conky updates between refreshes ]]

function photo_album(album_dir, xc, yc, w_max, h_max, t, update_interval)
    local function get_file_to_use()
        num_files = tonumber(conky_parse("${exec ls -A " .. album_dir .. " | wc -l}"))
        if num_files == nil then num_files = 0 end
        if num_files == 0 then return "none" end
    
        updates = tonumber(conky_parse("${updates}"))
        whole = math.ceil(updates/update_interval)
    
        if whole <= num_files
        then
            num_file_to_show = whole
        else
            whole = whole % num_files
            num_file_to_show = whole
        end
    
        return conky_parse("${exec ls " .. album_dir .. " | sed -n " .. num_file_to_show .. "p}")
    end

    function init_drawing_surface()
        imlib_set_cache_size(4096 * 1024)
        imlib_context_set_dither(1)
    end

    function draw_frame()
        cairo_rectangle(cr, xc - width/2 - t, yc - height/2 - t, width + 2*t, height + 2*t)
        cairo_set_source_rgba(cr, 1, 1, 1, 0.8)
        cairo_fill(cr)   
    end

    function draw_image()
        init_drawing_surface()
    
        image = imlib_load_image(album_dir .. filename)
        if image == nil then return end
        imlib_context_set_image(image)
	
    	w_img, h_img = imlib_image_get_width(), imlib_image_get_height()
    	if w_img >= h_img
    	then
    	    width = w_max - 2*t
    	    height = width * (h_img/w_img)
    	else
    	    height = h_max - 2*t
    	    width = height * (w_img/h_img)
    	end
    	
    	draw_frame()
    	
    	buffer = imlib_create_image(width, height)
    	imlib_context_set_image(buffer)
    	
    	imlib_blend_image_onto_image(image, 0, 0, 0, w_img, h_img, 0, 0, width, height)
    	imlib_context_set_image(image)
    	imlib_free_image()
    	
    	imlib_context_set_image(buffer)
    	imlib_render_image_on_drawable(xc - width/2, yc - height/2)
    	imlib_free_image()
    end

    if conky_window == nil then return end
    filename = get_file_to_use()
    if filename == "none"
    then
        print(album_dir .. ": No files found")
    else
        draw_image()
    end
end

--[[ END PHOTO ALBUM WIDGET ]]



--[[ RING (COUNTER-CLOCKWISE) WIDGET ]]
--[[ v1.1 by londonali1010 (2009) ]]
--[[ Options (name, arg, max, bg_colour, bg_alpha, xc, yc, radius, thickness, start_angle, end_angle):
	"name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
	"arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
	"max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
	"bg_colour" is the colour of the base ring.
	"bg_alpha" is the alpha value of the base ring.
	"fg_colour" is the colour of the indicator part of the ring.
	"fg_alpha" is the alpha value of the indicator part of the ring.
	"x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
	"radius" is the radius of the ring.
	"thickness" is the thickness of the ring, centred around the radius.
	"start_angle" is the starting angle of the ring, in degrees, counter-clockwise from top. Value can be either positive or negative.
	"end_angle" is the ending angle of the ring, in degrees, counter-clockwise from top. Value can be either positive or negative, but must be larger (e.g. more counter-clockwise) than start_angle. ]]

function ring_ccw(name, arg, max, bgc, bga, fgc, fga, xc, yc, r, t, sa, ea)
	local function rgb_to_r_g_b(colour, alpha)
		return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end
	
	local function draw_ring(pct)
		local angle_0 = sa * (2 * math.pi/360) - math.pi/2
		local angle_f = ea * (2 * math.pi/360) - math.pi/2
		local pct_arc = pct * (angle_f - angle_0)

		-- Draw background ring

		cairo_arc_negative(cr, xc, yc, r, angle_0, angle_f)
		cairo_set_source_rgba(cr, rgb_to_r_g_b(bgc, bga))
		cairo_set_line_width(cr, t) 
		cairo_stroke(cr)
	
		-- Draw indicator ring

		cairo_arc_negative(cr, xc, yc, r, angle_0, angle_0 - pct_arc)
		cairo_set_source_rgba(cr, rgb_to_r_g_b(fgc, fga))
		cairo_stroke(cr)
	end
	
	local function setup_ring()
		local str = ''
		local value = 0
		
		str = string.format('${%s %s}', name, arg)
		str = conky_parse(str)
		
		value = tonumber(str)
		if value == nil then value = 0 end
		pct = value/max
		
		draw_ring(pct)
	end	
	
	local updates = conky_parse('${updates}')
	update_num = tonumber(updates)
	
	if update_num > 5 then setup_ring() end
end

--[[ END RING (COUNTER-CLOCKWISE) WIDGET ]]

function conky_widgets()
	if conky_window == nil then return end
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	cr = cairo_create(cs)
        photo_album('/home/chinmaya/Pictures', 100, 100, 320, 180, 10, 5)
	
	cairo_destroy(cr)
end
```
Can you help me out!!

---

### Post by wlourf on 2010-01-03
Hi, 

This is my attempt to use lua binding (but no cairo) in my conky . It is based on londonali's Photo Album but pictures are displayed as stacks in a messy way (the script create an image after each conky refresh with all photos previously displayed).

I have post this on a blog too : [http://u-scripts.blogspot.com/](http://u-scripts.blogspot.com/)

bye !

w.

Edit 22 Feb 2010:
v1.1 The script is updated and can now get images from deviant art website



[IMG]http://picasaweb.google.com/lh/photo/Z8epJOoc6b3E3q--IiY6uQ?authkey=Gv1sRgCIuWyZa_8OSYFg&feat=directlink[/IMG]


[IMG]http://picasaweb.google.com/lh/photo/3lIwvg1YZcTVjAH42sNFpQ?feat=directlink[/IMG]

---

### Post by londonali1010 on 2010-01-03
> **chinmaya_n said:**
> While i was trying to have the photo album thing i get this error:```
Conky: llua_do_call: function conky_widgets execution failed: ...e/chinmaya/.conkyscripts/conky_widgets_duplicate.lua:150: attempt to call global 'cairo_xlib_surface_create' (a nil value)
```
I can run that air clock! but this is giving problem! My .conkyrc
*snip*
And my conky_widgets_duplicate.lua (i copied the code from your script!):
*snip*
Can you help me out!!

Can you check that you have imlib2 bindings for Lua enabled in your version of Conky? Check via "conky -v" in terminal.

Also, make sure that you have
```
require 'imlib2'
```
at the start of your Lua script (next to "require 'cairo'").

> **wlourf said:**
> Hi, 

This is my attempt to use lua binding (but no cairo) in my conky . It is based on londonali's Photo Album but pictures are displayed as stacks in a messy way (the script create an image after each conky refresh with all photos previously displayed).

I have post this on a blog too : [http://u-scripts.blogspot.com/](http://u-scripts.blogspot.com/)

bye !

w.

I love those!!! How did you get the script to retain what the last picture was?

---

### Post by wlourf on 2010-01-04
> **londonali1010 said:**
> 
I love those!!! How did you get the script to retain what the last picture was?

Thanks, I used imlib2.
At first call of, the script  create an empty image /tmp/img.png (which has the size of the drop area) and draw the first file on it. At next calls the script do the same with /tmp/img.png and so on ...


Script to call the image :
```

if file == nil then
   x=imlib_create_image(w_max,h_max)
   imlib_context_set_image(x)
   imlib_image_set_has_alpha(1)
   imlib_save_image(image_tmp)
   imlib_free_image()
end
imageTmp = imlib_load_image(image_tmp)
imlib_context_set_image(imageTmp)

```Script to had new picture to the image and to save the image:
```

imlib_blend_image_onto_image(rot_img, 1, 0,0, w_img, h_img,dx,dy,width,height)

imlib_context_set_image(imageTmp)
imlib_save_image(image_tmp)

imlib_render_image_on_drawable(0,0)
```I didn't know imlib but I think we can get nices effects with it (and CPU use is not so important) :P

---

### Post by chinmaya_n on 2010-01-04
> **londonali1010 said:**
> Can you check that you have imlib2 bindings for Lua enabled in your version of Conky? Check via "conky -v" in terminal.

Also, make sure that you have
```
require 'imlib2'
```
at the start of your Lua script (next to "require 'cairo'").

Thanx for the reply!
I 've inserted that require 'cairo' in my script!  but it does not draw the photo album!
It shows like this:```
chinmaya@chinmaya-desktop:~$ conky
Conky: desktop window (20000a8) is subwindow of root window (104)
Conky: window type - override
Conky: drawing to created window (0x4800001)
Conky: drawing to double buffer
sed: -e expression #1, char 2: invalid usage of line address 0
sed: -e expression #1, char 2: invalid usage of line address 0
sed: -e expression #1, char 2: invalid usage of line address 0
sed: -e expression #1, char 2: invalid usage of line address 0
sed: -e expression #1, char 2: invalid usage of line address 0
sed: -e expression #1, char 2: invalid usage of line address 0

```
I've that imlib2 :```
chinmaya@chinmaya-desktop:~$ conky -v
Conky 1.7.2 compiled Fri Oct 23 15:55:48 UTC 2009 for Linux 2.6.24-23-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

```
My .conkyrc: ```

background no

cpu_avg_samples 2
net_avg_samples 1
    
use_xft yes
xftfont Radio Space:size=45
uppercase no

xftalpha 0.1
update_interval 1.0
use_spacer none

total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
#own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes
no_buffers yes

gap_x 15
gap_y 30
  
draw_shades no
draw_outline no
draw_borders no
#draw_graph_borders no

default_color white
default_shade_color white
default_outline_color white
alignment top_right

minimum_size 600 80
maximum_width 600
  
#override_utf8_locale yes
#text_buffer_size 256

color1 5e97f6
color2 9ba2a7
color3 FFFFFF

#--lua load --#
lua_load ~/.conkyscripts/conky_widgets_duplicate.lua
lua_draw_hook_pre conky_widgets

### Now we start drawing ! ###

TEXT
${voffset -10}${alignr}${color2}${time %d %B %Y}

${voffset -90}${font Sans Bold:size=17} ${alignr} ${color1}CPU ${color2}${cpu cpu1}${color1} RAM ${color2}$memperc ${color1} DOWN ${color2}${downspeed eth0}${color1} UP ${color2}${upspeed eth0}

``` And my conky_widgets_duplicate.lua :```
require 'cairo'
require 'imlib2'

--[[ PHOTO ALBUM WIDGET ]]
--[[ by londonali1010 (2009) ]]
--[[ Options (album_dir, xc, yc, w_max, h_max, t, update_interval)
    "album_dir" is the directory containing the images for your photo album; please note that the path must be absolute (e.g. no "~")
    "xc" and "yc" are the coordinates of the centre of the photo album, relative to the top left corner of the Conky window, in pixels
    "w_max" and "h_max" are the maximum dimensions, in pixels, that you want the widget to be.  The script will ensure that the photo album fits inside the box bounded by w_max and h_max
    "t" is the thickness of the frame, in pixels
    "update_interval" is the number of Conky updates between refreshes ]]

function photo_album(album_dir, xc, yc, w_max, h_max, t, update_interval)
    local function get_file_to_use()
        num_files = tonumber(conky_parse("${exec ls -A " .. album_dir .. " | wc -l}"))
        if num_files == nil then num_files = 0 end
        if num_files == 0 then return "none" end
    
        updates = tonumber(conky_parse("${updates}"))
        whole = math.ceil(updates/update_interval)
    
        if whole <= num_files
        then
            num_file_to_show = whole
        else
            whole = whole % num_files
            num_file_to_show = whole
        end
    
        return conky_parse("${exec ls " .. album_dir .. " | sed -n " .. num_file_to_show .. "p}")
    end

    function init_drawing_surface()
        imlib_set_cache_size(4096 * 1024)
        imlib_context_set_dither(1)
    end

    function draw_frame()
        cairo_rectangle(cr, xc - width/2 - t, yc - height/2 - t, width + 2*t, height + 2*t)
        cairo_set_source_rgba(cr, 1, 1, 1, 0.8)
        cairo_fill(cr)   
    end

    function draw_image()
        init_drawing_surface()
    
        image = imlib_load_image(album_dir .. filename)
        if image == nil then return end
        imlib_context_set_image(image)
	
    	w_img, h_img = imlib_image_get_width(), imlib_image_get_height()
    	if w_img >= h_img
    	then
    	    width = w_max - 2*t
    	    height = width * (h_img/w_img)
    	else
    	    height = h_max - 2*t
    	    width = height * (w_img/h_img)
    	end
    	
    	draw_frame()
    	
    	buffer = imlib_create_image(width, height)
    	imlib_context_set_image(buffer)
    	
    	imlib_blend_image_onto_image(image, 0, 0, 0, w_img, h_img, 0, 0, width, height)
    	imlib_context_set_image(image)
    	imlib_free_image()
    	
    	imlib_context_set_image(buffer)
    	imlib_render_image_on_drawable(xc - width/2, yc - height/2)
    	imlib_free_image()
    end

    if conky_window == nil then return end
    filename = get_file_to_use()
    if filename == "none"
    then
        print(album_dir .. ": No files found")
    else
        draw_image()
    end
end

--[[ END PHOTO ALBUM WIDGET ]]



--[[ RING (COUNTER-CLOCKWISE) WIDGET ]]
--[[ v1.1 by londonali1010 (2009) ]]
--[[ Options (name, arg, max, bg_colour, bg_alpha, xc, yc, radius, thickness, start_angle, end_angle):
	"name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
	"arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
	"max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
	"bg_colour" is the colour of the base ring.
	"bg_alpha" is the alpha value of the base ring.
	"fg_colour" is the colour of the indicator part of the ring.
	"fg_alpha" is the alpha value of the indicator part of the ring.
	"x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
	"radius" is the radius of the ring.
	"thickness" is the thickness of the ring, centred around the radius.
	"start_angle" is the starting angle of the ring, in degrees, counter-clockwise from top. Value can be either positive or negative.
	"end_angle" is the ending angle of the ring, in degrees, counter-clockwise from top. Value can be either positive or negative, but must be larger (e.g. more counter-clockwise) than start_angle. ]]

function ring_ccw(name, arg, max, bgc, bga, fgc, fga, xc, yc, r, t, sa, ea)
	local function rgb_to_r_g_b(colour, alpha)
		return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end
	
	local function draw_ring(pct)
		local angle_0 = sa * (2 * math.pi/360) - math.pi/2
		local angle_f = ea * (2 * math.pi/360) - math.pi/2
		local pct_arc = pct * (angle_f - angle_0)

		-- Draw background ring

		cairo_arc_negative(cr, xc, yc, r, angle_0, angle_f)
		cairo_set_source_rgba(cr, rgb_to_r_g_b(bgc, bga))
		cairo_set_line_width(cr, t) 
		cairo_stroke(cr)
	
		-- Draw indicator ring

		cairo_arc_negative(cr, xc, yc, r, angle_0, angle_0 - pct_arc)
		cairo_set_source_rgba(cr, rgb_to_r_g_b(fgc, fga))
		cairo_stroke(cr)
	end
	
	local function setup_ring()
		local str = ''
		local value = 0
		
		str = string.format('${%s %s}', name, arg)
		str = conky_parse(str)
		
		value = tonumber(str)
		if value == nil then value = 0 end
		pct = value/max
		
		draw_ring(pct)
	end	
	
	local updates = conky_parse('${updates}')
	update_num = tonumber(updates)
	
	if update_num > 5 then setup_ring() end
end

--[[ END RING (COUNTER-CLOCKWISE) WIDGET ]]

function conky_widgets()
	if conky_window == nil then return end
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	cr = cairo_create(cs)
        photo_album('/home/chinmaya/Pictures', 100, 100, 320, 180, 10, 5)
	
	cairo_destroy(cr)
end
```
Ha Ha this is my longest post ever ;)
Sry for such a long post!!:P

---

### Post by Twilight in Zero on 2010-01-09
Hi there. I'm using londonali's conky_widgets script to create translucent windows behind my conkies. Well, for my Quod Libet conky, this happens:

[IMG]http://omploader.org/vMzdtYg/blockedalbumart.png[/IMG]

The image is behind the window. How can I fix this?

Here's the config for the Quod Libet conky.
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_colour 3c3c3c
own_window_title tizconkyql
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background yes
double_buffer yes
use_spacer none
update_interval 3.0

use_xft yes
xftfont UME P Gothic S5:size=10
xftalpha 1.0
override_utf8_locale yes
uppercase no
default_color white
color0 white
color1 8fc4cc

draw_shades yes
default_outline_color black
default_shade_color black
draw_outline no 
draw_borders no
draw_graph_borders no
minimum_size 160 12
maximum_width 160
imlib_cache_size 0
#border_margin 0
#border_width 0
border_inner_margin 2
border_outer_margin 2

alignment bottom_left
gap_x 4
gap_y 80

lua_load ~/.config/conky/ql_conky_widgets.lua
lua_draw_hook_pre widgets

TEXT
${if_existing /home/trent/.quodlibet/control}${if_existing /home/trent/.quodlibet/current.cover}${image /home/trent/.quodlibet/current.cover -p 10,2 -s 140x140}${voffset 146}$endif$color1${execp quodlibet --print-playing 'Title  $color0${alignr}<title>
${color1}Artist  $color0${alignr}<artist>
${color1}Album  $color0${alignr}<album>'}${else}${color1}Quod Libet is not running.$endif

```

And the relevant part of the conky_widgets lua script. I have the rectange draw off of the window so that only the right side has rounded corners.
```
function conky_widgets()
	if conky_window == nil then return end
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	cr = cairo_create(cs)

	round_rect(-20, 0, conky_window.width + 20, conky_window.height, 20, 0x3c3c3c, 0.7)
	cairo_destroy(cr)
end
```

Thanks in advance for your help! :)

---

### Post by londonali1010 on 2010-01-10
I suspect that you may have to draw the picture in Lua using imlib2 bindings...If you look at the photo_album widget, you'll see the syntax you need to do it.

Hope this helps!

---

### Post by wlourf on 2010-01-10
Hi,

This is another attempt to use cairo with lua (without imlib). It's derivated from clock air from londonali (thanks). This script draw only hands of the clock but with nices effects (IMHO ;))

---

### Post by londonali1010 on 2010-01-10
> **wlourf said:**
> Hi,

This is another attempt to use cairo with lua (without imlib). It's derivated from clock air from londonali (thanks). This script draw only hands of the clock but with nices effects (IMHO ;))

Ooooh, yes, very nice :) You've really got a hang of the Cairo thing...I'm struggling with drop shadows at the moment, I'm sure there's an easy way to do them, but I can only think of difficult ways! Yours are gorgeous :)

---

### Post by Twilight in Zero on 2010-01-10
> **londonali1010 said:**
> I suspect that you may have to draw the picture in Lua using imlib2 bindings...If you look at the photo_album widget, you'll see the syntax you need to do it.

Hope this helps!

It did help. I couldn't find documentation for the lua bindings, just the original imlib, so it took a while to figure out, but I managed. It's drawing on top of the rectangle now, but now I have a different problem. The album art won't change now. No matter which song I change to, I still have the album art from the first song I listen to. I actually experienced this same problem when I tried to use your own photo_album widget to get around my first problem. It also put an ugly white line on the bottom of non-square images, but that's probably intentional due to the whole framing thing.

Anyway, here's my album art function:
```
function draw_aa(filename, x, y, w, h)
	imlib_set_cache_size(0)
        imlib_context_set_dither(1)
        image = imlib_load_image(filename)
        if image == nil then return end
        imlib_context_set_image(image)
	scaled = imlib_create_cropped_scaled_image(0, 0, imlib_image_get_width(), imlib_image_get_height(), w, h)
	imlib_free_image()
	imlib_context_set_image(scaled)
    	imlib_render_image_on_drawable(x, y)
    	imlib_free_image()
end
```

Again, your help is greatly appreciated. :)

---

### Post by Hitaka on 2010-01-13
I have a problem with conky 1.7.2+lua+cairo on Fedora 12 x86_64
```

conky -v
Conky 1.7.2 compiled Tue Aug 25 10:34:53 EDT 2009 for Linux 2.6.18-128.4.1.el5xen (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib64/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * Audacious
  * MPD

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * wireless
  * support for IBM/Lenovo notebooks
  * config-output
  * ALSA mixer support
  * apcupsd
  * iostats
  * Lua

  Lua bindings:
   * Cairo

Lua 5.1.4
tolua++-1.0.92
cairo-1.8.8-3

```When I run conky without lua and cairo all is well but if I enable lua+cairo (eg clock_rings-v1.1.1.lua) got error
```

Conky: llua_load: error loading module 'cairo' from file '/usr/lib64/conky/libcairo.so': 
/usr/lib64/conky/libcairo.so: undefined symbol: tolua_isvaluenil

```I searched in google, wrote in fedoraforum.org. I can not figure out where is the error in cairo lua or tolua + +. Compile conky 1.7.2 from source and conky 1.8.0 but the error remains the same. Please help me understand this error and to remove

---

### Post by dk75 on 2010-01-13
show result of this
```

cat /usr/include/tolua++.h |awk '/LUA_REGISTRYINDEX/ {gsub(/[^0-9]/,""); print $NF}'

```

---

### Post by Hitaka on 2010-01-13
[Hitaka@localhost ~]$ cat /usr/include/tolua++.h |awk '/LUA_REGISTRYINDEX/ {gsub(/[^0-9]/,""); print $NF}'
51
[Hitaka@localhost ~]$

---

### Post by dk75 on 2010-01-15
did you compiled tolua++ themselves? or is it from system package repository?

---

### Post by wlourf on 2010-01-16
Hello,

**In a Lua Script, is there a way to save variables between two calls of the script?**

I try to explain : 
For example, in my calendar script [(here)]("http://ubuntuforums.org/showpost.php?p=8665537&postcount=127") I need to check the date of the day on a regular basis (10 secondes) in order to update the calendar after midnight. If the date at T is the same as T - 10 seconds, then it is not necessary to redraw the calendar (I think I can call a PNG created by the script).
But if the date at T is different from T-10 seconds, then I draw a new calendar. 
So, to keep the date at T-10, I write it in a text file. What do you think about this method? Is there a better way to do that ?
Also, I think it's faster to call a PNG file than to draw again the calendar with Cairo, right?

For example, I wrote this script for testing purpose : (changes are detected for MINUTES, not DAYS)
```
function conky_start_test()

var_file="/tmp/var_file.txt"

if conky_window==nil then return end
    s = os.time(t)
    dt = os.date("%Y%m%d%M",s)

    file = io.open(var_file,"r")
    if file == nil then
        print ("update : ",conky_parse('${updates}'),"file does not exist, will be created")
        write_variable(var_file,dt)
    else
        --print ("read date from " .. var_file)
        file = io.open(var_file,"r")
        first_line = file:read("*l")
        if first_line ~= dt then
            print (os.date("%H%M%S"), "variable has changed, do the stuff here")
            --for example draw the conky and save it as png
            write_variable(var_file, dt)
        else
            print  (os.date("%H%M%S"),"variable didn't changed , do nothing")
            --for example, don't draw the conky but call the previous png, should be faster ?
        end
    end
end

function write_variable(file, txt)
--write some text to file
    io.output(io.open(file,"w"))
    io.write(txt)
    io.close()
    print ("date has been writen in " .. file)
end

```and the conky with refresh every seconds :

```
# -- Conky settings -- #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #

own_window yes
#own_window_type desktop
own_window_transparent yes
#own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 1020 600
maximum_width 1000

alignment tm
gap_x 10
gap_y 0

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# -- Text settings -- #
use_xft yes
xftfont Santana:size=24
xftalpha 0.8

uppercase no

default_color FFFFFF

# -- Lua Load -- #
lua_load ~/scripts/test/test.lua
lua_draw_hook_pre start_test

TEXT
updates = ${updates}
${time %Y%m%d %H%M%S}
```

---

### Post by Hitaka on 2010-01-16
> **dk75 said:**
> did you compiled tolua++ themselves? or is it from system package repository?
No, tolua++ and cairo are from repo I compile only conky 1.7.2 Test, ERROR and uninstal, then compile conky 1.8 - ERROR again, and again uninstal Now my conky 1.7.2 is from distribution repo

---

### Post by dk75 on 2010-01-16
> **Hitaka said:**
> No, tolua++ and cairo are from repo I compile only conky 1.7.2 Test, ERROR and uninstal, then compile conky 1.8 - ERROR again, and again uninstal Now my conky 1.7.2 is from distribution repo

I'm asking because I've got problem with running Cairo or IMLIB2 LUA scripts when I've compiled tolua++ wrongly. There was no error when tolua++ compiled and there was no error with Conky compilation. I've got Conky with lua-cairo and lua-imlib2 bindings reported but when cairo/imlib lua script loaded then I've got similar errors as you.

> **wlourf said:**
> Hello,

**In a Lua Script, is there a way to save variables between two calls of the script?**

Yes.
Every variable defined outside functions (preferably at the beginning of the script) are global and are remembered between Conky refresh.

```

-- LUA global variable example
do
   myvariable = 1

   function conky_lua_test(x)
      if myvariable > x then
         print("\tVariable value reached max: " .. myvariable)
         myvariable = 1
      else
         print("\tVariable value: " .. myvariable)
         myvariable = myvariable + 1
      end
   end

   function conky_main()
      conky_lua_test(6)
   end
end

```

---

### Post by londonali1010 on 2010-01-17
> **dk75 said:**
> ...
Every variable defined outside functions (preferably at the beginning of the script) are global and are remembered between Conky refresh.
...

REALLY?! How did I not know this? It will make some things a lot easier! Especially since I usualy define everything as global because I'm not very good at passing variables between subroutines... :S Can you tell I'm not a coder?!

---

### Post by mobilediesel on 2010-01-17
> **londonali1010 said:**
> REALLY?! How did I not know this? It will make some things a lot easier! Especially since I usualy define everything as global because I'm not very good at passing variables between subroutines... :S Can you tell I'm not a coder?!

Sometimes the best way to learn is when you sit back and say "Holy @*#& I've been doing that the hard way!" :lol:

Keep up with the Lua and you'll be able to call yourself a coder. I mostly do Bash scripts so I only consider myself *kinda* a coder. :D

---

### Post by dk75 on 2010-01-17
Actually every variables that isn't declared as local (by **local** command or in function definition like **function myfunction(myvariable)**) are global - I've checked it out today:
```

-- LUA global variable example
do
   function conky_lua_test(x)
      if myvariable == nil then myvariable = 1 end
      if myvariable > x then
         print("\tVariable value reached max:",myvariable)
         myvariable = 1
      else
         print("\tVariable value:",myvariable)
         myvariable = myvariable + 1
      end
   end

   function conky_main()
      conky_lua_test(6)
      print("\t\"x\" variable:",x)
   end
end

```

---

### Post by wlourf on 2010-01-17
> **dk75 said:**
> Actually every variables that isn't declared as local (by **local** command or in function definition like **function myfunction(myvariable)**) are global - 

Thanks for your explanations and your example ! 
I have another question about Cairo : I would like to draw an image and keep it in memory for later use, not on the hard disk (with cairo_surface_write_to_png()).
In the documentation, there is this function that should be fine no ? 
```

[LIST]
[*][C]   [cairo_status_t]("http://www.dynaset.org/dogusanh/luacairo.html#cairo_status_t") cairo_surface_write_to_png_stream ([cairo_surface_t]("http://www.dynaset.org/dogusanh/luacairo.html#cairo_surface_t") *surface, [cairo_write_func_t]("http://www.dynaset.org/dogusanh/luacairo.html#cairo_write_func_t") write_func, void *closure);
[Lua] not implemente
[/LIST]

```I think this function is now implemented in Lua because I have no errors on his name but i get errors with the arguments.
For example, I do that :
```
cairo_surface_write_to_png_streams(cs2,io.write)
```the error is 
```
Conky: llua_do_call: function conky_draw_calendar execution failed: /home/wlourf/scripts/cal3/calendar.lua:261: error in function 'cairo_surface_write_to_png_stream'.
     argument #2 is 'function'; 'cairo_write_func_t' expected.

```To do short : **How to use the cairo_surface_write_to_png_stream function** ??

](*,)

bye

---

### Post by dk75 on 2010-01-18
for sure, **io.write** isn't the **cairo_write_funct_t**

There is a lot of 'C' or Python or Perl examples but none for LUA.

---

### Post by Twilight in Zero on 2010-01-24
I'm still having problems with this.

> **Twilight in Zero said:**
> It did help. I couldn't find documentation for the lua bindings, just the original imlib, so it took a while to figure out, but I managed. It's drawing on top of the rectangle now, but now I have a different problem. The album art won't change now. No matter which song I change to, I still have the album art from the first song I listen to. I actually experienced this same problem when I tried to use your own photo_album widget to get around my first problem. It also put an ugly white line on the bottom of non-square images, but that's probably intentional due to the whole framing thing.

Anyway, here's my album art function:
```
function draw_aa(filename, x, y, w, h)
	imlib_set_cache_size(0)
        imlib_context_set_dither(1)
        image = imlib_load_image(filename)
        if image == nil then return end
        imlib_context_set_image(image)
	scaled = imlib_create_cropped_scaled_image(0, 0, imlib_image_get_width(), imlib_image_get_height(), w, h)
	imlib_free_image()
	imlib_context_set_image(scaled)
    	imlib_render_image_on_drawable(x, y)
    	imlib_free_image()
end
```

Again, your help is greatly appreciated. :)

---

### Post by dk75 on 2010-01-24
"imlib_cache_size 0" in Conky config file above "TEXT" line

---

### Post by Twilight in Zero on 2010-01-24
> **dk75 said:**
> "imlib_cache_size 0" in Conky config file above "TEXT" line

I already have that.

---

### Post by tkdryan on 2010-01-25
Thanks to londonali1010 for posting this! Here's what I've done with mine, along with my conky and lua scripts. I had to import my wallpaper into GIMP and overlay the white lines because I couldn't figure out how to get it set correctly in conky in addition to my other stuff. If someone knows an easy way to do it, that'd be sweet.

---

### Post by pw_f100_220 on 2010-01-26
I now have widgets working, but I really prefer (and have already made) the options to functions format like the original(?) rings script such as:
        {
                name='time',
                arg='%S',
                max=60,
                bg_colour=0xffffff,
                bg_alpha=0.1,
                fg_colour=0xffffff,
                fg_alpha=0.6,
                x=165, y=170,
                radius=62,
                thickness=5,
                start_angle=212,
                end_angle=360
        },

can the widgets script incorporate options in the same way?

---

### Post by niraj2709 on 2010-01-28
hello friends 
i am trying to run lua script in conky, however when i try to run it i get the following error:

niraj@niraj-laptop:~$ conky
Conky: /etc/conky/conky.conf: 45: no such configuration: 'lua_load'
Conky: /etc/conky/conky.conf: 46: no such configuration: 'lua_draw_hook_pre'
Conky: unknown variable 
Conky: forked to background, pid is 11715
niraj@niraj-laptop:~$ 
Conky: desktop window (110) is root window
Conky: window type - desktop
Conky: drawing to created window (0x1c00001)
Conky: drawing to double buffer





my conky.rc is

# conky configuration
#
# The list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.
#
# For ideas about how to modify conky, please see:
# [http://crunchbanglinux.org/forums/topic/59/my-conky-config/](http://crunchbanglinux.org/forums/topic/59/my-conky-config/)
#
# For help with conky, please see:
# [http://crunchbanglinux.org/forums/topic/2047/conky-help/](http://crunchbanglinux.org/forums/topic/2047/conky-help/)
#
# Enjoy! :)
##############################################
#  Settings
##############################################
background yes
use_xft yes
xftfont Sans:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 240
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 12
gap_y 12
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

lua_load /home/niraj/scripts/clock_rings.lua
    lua_draw_hook_pre clock_rings


##############################################
#  Output
##############################################


TEXT
${font Sans:size=12}${color white}$alignc debian-crunchbang ${color white}
${hr}
${color white}$alignc${font Sans:size=12}${time %H:%M:%S}${font}

${color white}$alignc${font :size=8}${time %A %d %B %Y}${color white}

${font Mono:size=8}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color yellow}'"$DJS"'${color}'" "/}
${font sans:size=8}${color white}SYSTEM INFO ${color white}${hr} $font$
host$alignr$nodename
uptime$alignr$uptime
cpu $alignr ${cpu cpu1}% 
${cpubar cpu1}
ram         $mem / $memmax $alignr $memperc%
$membar
swap      ${swap} / ${swapmax} $alignr ${swapperc}%
${swapbar}
disk       ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}






 

and my lua scripts are in my home folder (/home/niraj/scripts)


how to set this thing up running ??
please help me, i am not much familiar with conky/lua
thanks

---

### Post by dmillerct on 2010-01-28
> **niraj2709 said:**
> hello friends 
i am trying to run lua script in conky, however when i try to run it i get the following error:

niraj@niraj-laptop:~$ conky
Conky: /etc/conky/conky.conf: 45: no such configuration: 'lua_load'
Conky: /etc/conky/conky.conf: 46: no such configuration: 'lua_draw_hook_pre'
Conky: unknown variable 
Conky: forked to background, pid is 11715
niraj@niraj-laptop:~$ 
Conky: desktop window (110) is root window
Conky: window type - desktop
Conky: drawing to created window (0x1c00001)
Conky: drawing to double buffer





my conky.rc is

# conky configuration
#
# The list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.
#
# For ideas about how to modify conky, please see:
# [http://crunchbanglinux.org/forums/topic/59/my-conky-config/](http://crunchbanglinux.org/forums/topic/59/my-conky-config/)
#
# For help with conky, please see:
# [http://crunchbanglinux.org/forums/topic/2047/conky-help/](http://crunchbanglinux.org/forums/topic/2047/conky-help/)
#
# Enjoy! :)
##############################################
#  Settings
##############################################
background yes
use_xft yes
xftfont Sans:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 240
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 12
gap_y 12
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

lua_load /home/niraj/scripts/clock_rings.lua
    lua_draw_hook_pre clock_rings


##############################################
#  Output
##############################################


TEXT
${font Sans:size=12}${color white}$alignc debian-crunchbang ${color white}
${hr}
${color white}$alignc${font Sans:size=12}${time %H:%M:%S}${font}

${color white}$alignc${font :size=8}${time %A %d %B %Y}${color white}

${font Mono:size=8}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color yellow}'"$DJS"'${color}'" "/}
${font sans:size=8}${color white}SYSTEM INFO ${color white}${hr} $font$
host$alignr$nodename
uptime$alignr$uptime
cpu $alignr ${cpu cpu1}% 
${cpubar cpu1}
ram         $mem / $memmax $alignr $memperc%
$membar
swap      ${swap} / ${swapmax} $alignr ${swapperc}%
${swapbar}
disk       ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}






 

and my lua scripts are in my home folder (/home/niraj/scripts)


how to set this thing up running ??
please help me, i am not much familiar with conky/lua
thanks

It looks like the issue could be with your conky version.

Can you post the output of 'conky -v' please. Also what distro are you running / version?

---

### Post by niraj2709 on 2010-01-28
thanks for prompt reply

niraj@niraj-laptop:~$ conky -v
Conky 1.7.1.1 compiled Mon Dec 14 06:44:33 UTC 2009 for Linux 2.6.31.6-dsa-ia32 (i686)

Compiled in features:

System config file: /etc/conky/conky.conf

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * RSS
  * wireless
  * support for IBM/Lenovo notebooks
  * config-output
  * ALSA mixer support
  * apcupsd
niraj@niraj-laptop:~$ 


i am running debian testing

thanks

---

### Post by dmillerct on 2010-01-28
> **niraj2709 said:**
> thanks for prompt reply

niraj@niraj-laptop:~$ conky -v
Conky 1.7.1.1 compiled Mon Dec 14 06:44:33 UTC 2009 for Linux 2.6.31.6-dsa-ia32 (i686)

Compiled in features:

System config file: /etc/conky/conky.conf

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * RSS
  * wireless
  * support for IBM/Lenovo notebooks
  * config-output
  * ALSA mixer support
  * apcupsd
niraj@niraj-laptop:~$ 


i am running debian testing

thanks

ya, the version you are running does not have lua/ciaro bindings. Look for a deb file for 1.7.2 it is stable and should have all the features you need.

---

### Post by niraj2709 on 2010-01-28
thanks
however i am not able to find a deb file for debian. even the sid pakages have conky 1.7.1 and not 1.7.2
i have downloaded tar file from the main conky site, but how should i install it ?
thanks once again

now i feel i should have used ubuntu instead of debian, anyways....
we all learn from our mistakes

---

### Post by dmillerct on 2010-01-28
> **niraj2709 said:**
> thanks
however i am not able to find a deb file for debian. even the sid pakages have conky 1.7.1 and not 1.7.2
i have downloaded tar file from the main conky site, but how should i install it ?
thanks once again

now i feel i should have used ubuntu instead of debian, anyways....
we all learn from our mistakes

You may need to compile your own then. I am not sure how to do this, someone else might have a better solution for you.

---

### Post by niraj2709 on 2010-01-28
thanks for your help

---

### Post by wlourf on 2010-01-29
> **niraj2709 said:**
> thanks for your help

My experience :  for version 1.7.2, I used the deb from this [post]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8080064&postcount=9716") and it works fine. 
It looks like this deb is no more available but you can try 1.8.0 wich is beta I guess.

---

### Post by dmillerct on 2010-01-29
> **wlourf said:**
> My experience :  for version 1.7.2, I used the deb from this [post]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8080064&postcount=9716") and it works fine. 
It looks like this deb is no more available but you can try 1.8.0 wich is beta I guess.

I tried 1.80_rc1 and it was not good. I think rc2 is floating around somewhere but I have not tried it.

---

### Post by wlourf on 2010-01-31
hello!

 Does anyone knows the way to apply filter with lua and imlib?

 Lua can use the function **imlib_apply_filter** but how to use it and where find filters (i am looking for a blur filter)? 

I have three filters in /usr/lib/imlib2/filters but don't know how to use it :
/usr/lib/imlib2/filters/bumpmap.so
/usr/lib/imlib2/filters/colormod.so
/usr/lib/imlib2/filters/testfilter.so[B]

Thanks !


[/B]

---

### Post by pw_f100_220 on 2010-02-01
Is it possible to add an "if" to a specific object (ring) in the widgets script?  I want this specific ring to show only when mpd is playing like the ${if_mpd_playing} option in conky.

```
cr = cairo_create(cs)
ring (cr, 'mpd_percent', '', 100, 0x000000, 0.2, 0xcccccc, 0.7, 165, 170, 135, 15, -130, 90)
cairo_destroy(cr)
```

Any ideas?

---

### Post by wlourf on 2010-02-02
> **pw_f100_220 said:**
> Is it possible to add an "if" to a specific object (ring) in the widgets script?  I want this specific ring to show only when mpd is playing like the ${if_mpd_playing} option in conky.

```
cr = cairo_create(cs)
ring (cr, 'mpd_percent', '', 100, 0x000000, 0.2, 0xcccccc, 0.7, 165, 170, 135, 15, -130, 90)
cairo_destroy(cr)
```Any ideas?
try this:
```

if conky_parse("${if_mpd_playing}") then
     ring (cr, 'mpd_percent', '', 100, 0x000000, 0.2, 0xcccccc, 0.7, 165, 170, 135, 15, -130, 90)
     cairo_destroy(cr)
end

```Not tested but this should work if conky_parse("${if_mpd_playing}") returns a boolean...

---

### Post by pw_f100_220 on 2010-02-02
try this:
```

if conky_parse("${if_mpd_playing}") then
     ring (cr, 'mpd_percent', '', 100, 0x000000, 0.2, 0xcccccc, 0.7, 165, 170, 135, 15, -130, 90)
     cairo_destroy(cr)
end

```Not tested but this should work if conky_parse("${if_mpd_playing}") returns a boolean...[/QUOTE]

Tested and no dice.  From other examples, the conky_parse(yada) could be applied to an entire function instead of a single created object. This makes me curious about simply copying the ring widget and giving it an if statement for mpd.  Then just called in the widgets script by ring_mpd(cr...).  Does that sound feasable?  This guy seems to have that idea:

[http://crunchbanglinux.org/forums/topic/6274/lua-script-conky-help/](http://crunchbanglinux.org/forums/topic/6274/lua-script-conky-help/)

 ...however I found this little snippet unrelated to conky:
```

  ct = cairo_create(cs);
  if(fontsize<=0){
    fontsize=height*15./792.;
    if(fontsize<5)fontsize=5;

```

it resembles the calling of an object ("cr = cairo_create(cs)) and is followed by an "if"...which is in lua I believe, based on this webpage:

[http://www.lua.org/pil/4.3.1.html](http://www.lua.org/pil/4.3.1.html)

However, I believe I'm starting to deep into the language to understand what's going on...grrrr.

---

### Post by wlourf on 2010-02-02
> **pw_f100_220 said:**
> try this:
```

if conky_parse("${if_mpd_playing}") then
     ring (cr, 'mpd_percent', '', 100, 0x000000, 0.2, 0xcccccc, 0.7, 165, 170, 135, 15, -130, 90)
     cairo_destroy(cr)
end

```Not tested but this should work if conky_parse("${if_mpd_playing}") returns a boolean...

Tested and no dice.  From other examples, the conky_parse(yada) could be applied to an entire function instead of a single created object. This makes me curious about simply copying the ring widget and giving it an if statement for mpd. .

and if you write if_mpd_playing in your conky?:
```
# -- Lua Load -- #
lua_load ~/scripts/test/test.lua
#lua_draw_hook_pre draw_ring
 
TEXT
${if_mpd_playing}
    ${lua mpd_ring}
${endif}

```and in your lua :

```
function conky_mpd_ring()
    if conky_window==nil then return end
cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    cr = cairo_create(cs)
    ring (cr, 'mpd_percent', '', 100, 0x00FF00, 1, 0xccFFcc, 1, 100, 100, 100, 15, 0, 360);
    cairo_destroy(cr)
end

```it works *almost* on my PC : the conky is blinking (it happens sometimes with others conkys so you should try on your own)
hth

---

### Post by pw_f100_220 on 2010-02-04
It draws nothing and returns this by itself in .lua:

```
Conky: llua_do_call: function conky_mpd_ring execution failed: /home/elias/.config/conkympd.lua:3: attempt to call global 'cairo_xlib_surface_create' (a nil value)

```

and with the ring widget it just gives a different line number.  they both refer to the line "cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)"

---

### Post by wlourf on 2010-02-05
> **pw_f100_220 said:**
> It draws nothing and returns this by itself in .lua:

```
Conky: llua_do_call: function conky_mpd_ring execution failed: /home/elias/.config/conkympd.lua:3: attempt to call global 'cairo_xlib_surface_create' (a nil value)

```and with the ring widget it just gives a different line number.  they both refer to the line "cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)"

for your error, just add
```
require 'cairo' 
```at the beginning of your Lua script

But it won't draw nothing because ${lua the_function} return a string and print it with conky (see [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)) . I tried it and the ring widget is executed but nothing is drawn, I don't know why, so if you find, tell us !

Thinking of little bit more, I found this way to do it : you have to pass a variable from the conky to the lua (done with mixer_mute for tests cause I don't have mpd):
First you set a flag to zero and change it if needed in the if statement.
I use 0 and 1, because $lua send strings, not booleans

```
## -- Lua Load -- #
lua_load ~/scripts/test/test.lua
lua_draw_hook_pre my_ring
 
TEXT
${lua my_flag 0}
${if_mixer_mute}
    ${updates} mixer mute
    ${lua my_flag 1}
${endif}

```And in the lua script :
You read the flag, which is global and draw the ring if it's true
```

function conky_my_flag(my_arg)
    flag = my_arg
    return ""
end

function conky_my_ring()
    if conky_window==nil then return end
    cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    cr = cairo_create(cs)
    print ("fonction ring",tonumber(flag)==1)
    if tonumber(flag)==1 then
        print ("draw ring")
        ring (cr, 'time', '%S', 60, 0x00FF00, 1, 0xccFFcc, 1, 100, 100, 50, 15, 0, 360);
    end
    cairo_destroy(cr)
end

--your ring widget here

```(Take care, the ring widget is drawn after the fifth update of the conky).
It's not an easy way so any improve is welcome ... but afterall, it's work :P

---

### Post by pw_f100_220 on 2010-02-05
Wonderful!  Took some fiddling to make it work for me within the conky widgets script.  But I now have lua rings that show up and some that require MPD to be playing or paused!!!  Boom!

wlourf!  You are my hero!  You do good work man.  

If anyone wants an "if" ring, put wlourf's flag in conky, then the flag function and this as an object in your conky widgets script (basically making his function an object for the "widgets" function by trimming it):

```
cr = cairo_create(cs)
print ("function ring",tonumber(flag)==1)
if tonumber(flag)==1 then
print ("draw ring")
ring (cr, 'mpd_percent', '', 100, 0x000000, 0.2, 0xcccccc, 0.7, 165, 170, 135, 15, -130, 90)
end
cairo_destroy(cr)

```

also, you can put multiple rings/objects before end to have multiple objects depend on the "1" flag.  :)

---

### Post by dmillerct on 2010-02-05
> **pw_f100_220 said:**
> Wonderful!  Took some fiddling to make it work for me within the conky widgets script.  But I now have lua rings that show up and some that require MPD to be playing or paused!!!  Boom!

wlourf!  You are my hero!  You do good work man.  

If anyone wants an "if" ring, put wlourf's flag in conky, then the flag function and this as an object in your conky widgets script (basically making his function an object for the "widgets" function by trimming it):

```
cr = cairo_create(cs)
print ("function ring",tonumber(flag)==1)
if tonumber(flag)==1 then
print ("draw ring")
ring (cr, 'mpd_percent', '', 100, 0x000000, 0.2, 0xcccccc, 0.7, 165, 170, 135, 15, -130, 90)
end
cairo_destroy(cr)

```

also, you can put multiple rings/objects before end to have multiple objects depend on the "1" flag.  :)

OK I am quite smashed right now (again too much slivovitz) when I sober up tomorrow afternoon I will be sure to try this. I have A LOT of "if" variables I would like to try with the ciaro rings.

---

### Post by pw_f100_220 on 2010-02-05
> **dmillerct said:**
> OK I am quite smashed right now (again too much slivovitz) when I sober up tomorrow afternoon I will be sure to try this. I have A LOT of "if" variables I would like to try with the ciaro rings.

most of my tweaking was done under the influence...but good luck with your morrow!

---

### Post by wlourf on 2010-02-06
> **pw_f100_220 said:**
> Wonderful!  Took some fiddling to make it work for me within the conky widgets script.  But I now have lua rings that show up and some that require MPD to be playing or paused!!!  Boom!

wlourf!  You are my hero!  You do good work man.  

If anyone wants an "if" ring, put wlourf's flag in conky, then the flag function and this as an object in your conky widgets script (basically making his function an object for the "widgets" function by trimming it):

```
cr = cairo_create(cs)
print ("function ring",tonumber(flag)==1)
if tonumber(flag)==1 then
print ("draw ring")
ring (cr, 'mpd_percent', '', 100, 0x000000, 0.2, 0xcccccc, 0.7, 165, 170, 135, 15, -130, 90)
end
cairo_destroy(cr)

```also, you can put multiple rings/objects before end to have multiple objects depend on the "1" flag.  :)

thanks you! pw_f100_220 \\:D/ I have to say that I am very inspired with this conky stuff since I use OpenBox. As you say, the flag is to use with any ${if ... endif} block in conkyrc. I hope we will see your conky screen soon.

---

### Post by pw_f100_220 on 2010-02-06
My lua is mostly for looks rather than information, so it's a bit busy.  First one with MPD playing, and second without.  I mostly just use it for managing volume (outside ring without MPD playing, shows PCM and Master).  

I dual screen so this is just the right head.  My background changes all the time, otherwise I would probably make it sit on her ear.  The lua changes a lot, too.  I may post an update later if it changes enough.

Fluxbox WM :)

---

### Post by chinmaya_n on 2010-02-08
> **pw_f100_220 said:**
> My lua is mostly for looks rather than information, so it's a bit busy.  First one with MPD playing, and second without.  I mostly just use it for managing volume (outside ring without MPD playing, shows PCM and Master).  

I dual screen so this is just the right head.  My background changes all the time, otherwise I would probably make it sit on her ear.  The lua changes a lot, too.  I may post an update later if it changes enough.

Fluxbox WM :)

I would like to have that conky! and background too ;)

---

### Post by mrpeachy on 2010-02-10
Hi

I may be misunderstanding what your trying to do re the if statement to get a ring display based on a condition...

but i have done something similar and i think this might be a less complicated solution

this line checks wether a laptop is plugged in and charging or not

in lua
onoff=conky_parse('${if_existing /sys/class/power_supply/ACAD/online}1${else}0${endif}')

your parsing the whole if statement in lua and getting a 1 or 0 back

then used
if onoff==1 then
else

Ignore me if i've missed the point (i was only brought to this thread because i was looking for a cairo blur effect :) )

---

### Post by wlourf on 2010-02-11
> **mrpeachy said:**
> 

in lua
onoff=conky_parse('${if_existing /sys/class/power_supply/ACAD/online}1${else}0${endif}')

your parsing the whole if statement in lua and getting a 1 or 0 back

then used
if onoff==1 then
else

Ignore me if i've missed the point (i was only brought to this thread because i was looking for a cairo blur effect :) )

Good and simpe idea, thanks for sharing, it works fine. (just write if onoff=="1" because onoff is a string)
And do you find the blur effect?

---

### Post by mrpeachy on 2010-02-11
no problem
I have found that the if works without the quotes
just  if onoff==1 then ( i think... now i'll have to go check!)

re the blur... no luck yet, or at least nothing I know how to implement.

i was thinking along the line of seeing if you can export the data from cairo to imlib2... 
you can use imlib2 to apply a blur filter to an image... or even export the cairo data to an image file and then display and blur the image with imlib2

but i havn't found out how to do that yet

---

### Post by wlourf on 2010-02-12
> **mrpeachy said:**
> 

re the blur... no luck yet, or at least nothing I know how to implement.

i was thinking along the line of seeing if you can export the data from cairo to imlib2... 
you can use imlib2 to apply a blur filter to an image... or even export the cairo data to an image file and then display and blur the image with imlib2

but i havn't found out how to do that yet

Hi MrPeachy !
To export data from cairo to imlib, I think you have to export cairo to a png file and import png in imlib.
Look at theses functions in lua :
```
cairo_surface_write_to_png()
imlib_load_image()

```Maybe there is another way, but at least it works, I used this method for my "calendar wheel" script if you 're looking for an example, it's [here]("http://u-scripts.blogspot.com/2010/01/calendar-wheel-v12.html").

But how do you blur an image with imlib ??

Thanks

---

### Post by mrpeachy on 2010-02-12
I thought I had read about a blur filter with imlib2... but maybe it was something else:
heres one place that mentions it:

[http://asbradbury.org/projects/lua-imlib2/doc/](http://asbradbury.org/projects/lua-imlib2/doc/)
search for blur... says
**img:blur(radius)**

  Blurs the image. A radious value of 0 has no effect. 1 and above determine  the blur matrix radius that determines how much to blur the image.

but now im not sure that this might require the lua-imlib2 package created by the author.

Or you could do your own "blur" effect, by calling multiple instances of the same image, altering their alpha value and overlaying them with slightly altered positions like this:
[[IMG]http://omploader.org/tM2phYg[/IMG]]("http://omploader.org/vM2phYg")
goes to
[[IMG]http://omploader.org/tM2phYw[/IMG]]("http://omploader.org/vM2phYw")
or another way to achieve a blur like effect would be to scale the image down, save it and then scale it back up again like this:
[[IMG]http://omploader.org/tM2phcw[/IMG]]("http://omploader.org/vM2phcw")
not as nice but quick and easy.

i havnt used imlib2 so i dont know if it can do the above either :)

---

### Post by wlourf on 2010-02-18
Hi all,

I need some advice for calling C code in a Lua script.

I am back with my attempt to draw an audio equalizer widget with conky (does this already exist ?)
This work is based on this widget (Impulse) for gnome : [https://launchpad.net/impulse.bzr](https://launchpad.net/impulse.bzr)

So, if I can't get something faster, I will post the code here.

Actually the Lua script call a python script which call the Impulse.so file.

So I think Lua should call directly the Impulse.so file but I have no skills in C and it's where problems begin ! First I read this [tuto]("http://www.wellho.net/mouth/1844_Calling-functions-in-C-from-your-Lua-script-a-first-HowTo.html") 

The conky is :
```
# -- Conky settings -- #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #

own_window yes
#own_window_type desktop
own_window_transparent yes
#own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_title with lua

border_inner_margin 0
border_outer_margin 0

minimum_size 200 300

alignment tm
gap_x 10
gap_y 0

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# -- Text settings -- #
use_xft yes
xftfont Santana:size=12
xftalpha 0.8

uppercase no

default_color FFFFFF


# -- Lua Load -- #
# SET THE PATH TO THE SCRIPT HERE
lua_load ~/scripts/equa1.1c/equalizer.lua
lua_draw_hook_pre main3

TEXT
with lua
cpu0 ${cpu cpu0}
cpu1 ${cpu cpu1}
update=0.1
mem ${mem}
up. ${updates}

```The Lua code to load the Impulse.so is :

```
require 'cairo'
function conky_main3()

    package.cpath = "./?.so"
    require "Impulse"
    if conky_window == nil then return end
    
    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    
    cr = cairo_create(cs)

    cairo_destroy(cr)
    cairo_surface_destroy(cs)
        
end
```After installing the packages libfftw3 and libpulsedev
I modified the Impulse.c file at the beginning :

```
/*
 *
 *+  Copyright (c) 2009 Ian Halpern
 *@  http://impulse.ian-halpern.com
 *
 *   This file is part of Impulse.
 *
 *   Impulse is free software: you can redistribute it and/or modify
 *   it under the terms of the GNU General Public License as published by
 *   the Free Software Foundation, either version 3 of the License, or
 *   (at your option) any later version.
 *
 *   Impulse is distributed in the hope that it will be useful,
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *   GNU General Public License for more details.
 *
 *   You should have received a copy of the GNU General Public License
 *   along with Impulse.  If not, see <http://www.gnu.org/licenses/>.
 */
/* 
wlourf 16.02.2010
added the 4 first lines
install libfftw3 libpulsedev package
*/

#include "lua/lua.h"
#include "lua/lualib.h"
#include "lua/lauxlib.h"
#include "stdio.h"

#include <pulse/pulseaudio.h>
#include <assert.h>
#include <string.h>
#include <fftw3.h>
#include <math.h>

#define CHUNK 1024

static const long fft_max[] = { 12317168L, 7693595L, 5863615L, 4082974L, 5836037L, 4550263L, 3377914L, 3085778L, 3636534L, 3751823L, 2660548L, 3313252L, 2698853L, 2186441L, 1697466L, 1960070L, 1286950L, 1252382L, 1313726L, 1140443L, 1345589L, 1269153L, 897605L, 900408L, 892528L, 587972L, 662925L, 668177L, 686784L, 656330L, 1580286L, 785491L, 761213L, 730185L, 851753L, 927848L, 891221L, 634291L, 833909L, 646617L, 804409L, 1015627L, 671714L, 813811L, 689614L, 727079L, 853936L, 819333L, 679111L, 730295L, 836287L, 1602396L, 990827L, 773609L, 733606L, 638993L, 604530L, 573002L, 634570L, 1015040L, 679452L, 672091L, 880370L, 1140558L, 1593324L, 686787L, 781368L, 605261L, 1190262L, 525205L, 393080L, 409546L, 436431L, 723744L, 765299L, 393927L, 322105L, 478074L, 458596L, 512763L, 381303L, 671156L, 1177206L, 476813L, 366285L, 436008L, 361763L, 252316L, 204433L, 291331L, 296950L, 329226L, 319209L, 258334L, 388701L, 543025L, 396709L, 296099L, 190213L, 167976L, 138928L, 116720L, 163538L, 331761L, 133932L, 187456L, 530630L, 131474L, 84888L, 82081L, 122379L, 82914L, 75510L, 62669L, 73492L, 68775L, 57121L, 94098L, 68262L, 68307L, 48801L, 46864L, 61480L, 46607L, 45974L, 45819L, 45306L, 45110L, 45175L, 44969L, 44615L, 44440L, 44066L, 43600L, 57117L, 43332L, 59980L, 55319L, 54385L, 81768L, 51165L, 54785L, 73248L, 52494L, 57252L, 61869L, 65900L, 75893L, 65152L, 108009L, 421578L, 152611L, 135307L, 254745L, 132834L, 169101L, 137571L, 141159L, 142151L, 211389L, 267869L, 367730L, 256726L, 185238L, 251197L, 204304L, 284443L, 258223L, 158730L, 228565L, 375950L, 294535L, 288708L, 351054L, 694353L, 477275L, 270576L, 426544L, 362456L, 441219L, 313264L, 300050L, 421051L, 414769L, 244296L, 292822L, 262203L, 418025L, 579471L, 418584L, 419449L, 405345L, 739170L, 488163L, 376361L, 339649L, 313814L, 430849L, 275287L, 382918L, 297214L, 286238L, 367684L, 303578L, 516246L, 654782L, 353370L, 417745L, 392892L, 418934L, 475608L, 284765L, 260639L, 288961L, 301438L, 301305L, 329190L, 252484L, 272364L, 261562L, 208419L, 203045L, 229716L, 191240L, 328251L, 267655L, 322116L, 509542L, 498288L, 341654L, 346341L, 451042L, 452194L, 467716L, 447635L, 644331L, 1231811L, 1181923L, 1043922L, 681166L, 1078456L, 1088757L, 1221378L, 1358397L, 1817252L, 1255182L, 1410357L, 2264454L, 1880361L, 1630934L, 1147988L, 1919954L, 1624734L, 1373554L, 1865118L, 2431931L };

static int16_t buffer[ CHUNK / 2 ], snapshot[ CHUNK / 2 ];
static size_t buffer_index = 0;

static pa_context *context = NULL;
static pa_stream *stream = NULL;
static pa_threaded_mainloop* mainloop = NULL;
static pa_io_event* stdio_event = NULL;
static pa_mainloop_api *mainloop_api = NULL;
static char *stream_name = NULL, *client_name = NULL, *device = NULL;

static pa_sample_spec sample_spec = {
    .format = PA_SAMPLE_S16LE,
    .rate = 44100,
    .channels = 2
};

static pa_stream_flags_t flags = 0;

static pa_channel_map channel_map;
static int channel_map_set = 0;


/* A shortcut for terminating the application */
static void quit( int ret ) {
    assert( mainloop_api );
    mainloop_api->quit( mainloop_api, ret );
}

static void get_source_info_callback( pa_context *c, const pa_source_info *i, int is_last, void *userdata ) {

    if ( is_last || device != NULL )
        return;

    assert(i);

    // snprintf(t, sizeof(t), "%u", i->monitor_of_sink);

    if ( i->monitor_of_sink != PA_INVALID_INDEX ) {

        device = pa_xstrdup( i->name );

        if ( ( pa_stream_connect_record( stream, device, NULL, flags ) ) < 0 ) {
            fprintf(stderr, "pa_stream_connect_record() failed: %s\n", pa_strerror(pa_context_errno(c)));
            quit(1);
        }
    }
}

/* This is called whenever new data may is available */
static void stream_read_callback(pa_stream *s, size_t length, void *userdata) {
    const void *data;
    assert(s);
    assert(length > 0);

    if (stdio_event)
        mainloop_api->io_enable(stdio_event, PA_IO_EVENT_OUTPUT);

    if (pa_stream_peek(s, &data, &length) < 0) {
        fprintf(stderr, "pa_stream_peek() failed: %s\n", pa_strerror(pa_context_errno(context)));
        quit(1);
        return;
    }

    assert(data);
    assert(length > 0);

    int excess = buffer_index * 2 + length - ( CHUNK );

    if ( excess < 0 ) excess = 0;

    memcpy( buffer + buffer_index, data, length - excess );
    buffer_index += ( length - excess ) / 2;

    if ( excess ) {
        memcpy( snapshot, buffer, buffer_index * 2 );
        buffer_index = 0;
    }

    pa_stream_drop(s);
}


static void context_state_callback(pa_context *c, void *userdata) {

    switch (pa_context_get_state(c)) {
        case PA_CONTEXT_CONNECTING:
        case PA_CONTEXT_AUTHORIZING:
        case PA_CONTEXT_SETTING_NAME:
            break;
        case PA_CONTEXT_READY:
            assert(c);
            assert(!stream);

            if (!(stream = pa_stream_new(c, stream_name, &sample_spec, channel_map_set ? &channel_map : NULL))) {
                fprintf(stderr, "pa_stream_new() failed: %s\n", pa_strerror(pa_context_errno(c)));
                quit(1);
            }

            pa_stream_set_read_callback(stream, stream_read_callback, NULL);

            pa_operation_unref( pa_context_get_source_info_list( c, get_source_info_callback, NULL ) );

            break;
        case PA_CONTEXT_TERMINATED:
            quit(0);
            break;

        case PA_CONTEXT_FAILED:
        default:
            fprintf(stderr, "Connection failure: %s\n", pa_strerror(pa_context_errno(c)));
            quit(1);
    }
}

void im_stop (void) {

    pa_threaded_mainloop_stop( mainloop );

    //printf( "exit\n" );
}

double *im_getSnapshot( int fft ) {

    static double magnitude[ CHUNK / 4 ];

    if ( ! fft ) {
        int i;
        for ( i = 0; i < CHUNK / 2; i += sample_spec.channels ) {
            magnitude[ i / sample_spec.channels ] = 0;
            int j;
            for ( j = 0; j < sample_spec.channels; j++ )
                magnitude[ i / sample_spec.channels ] += fabs( ( (double) snapshot[ i + j ] / ( pow( 2, 16 ) / 2 ) ) / sample_spec.channels );
        }
    } else {

        double *in;
        fftw_complex *out;
        fftw_plan p;

        in = (double*) malloc( sizeof( double ) * ( CHUNK / 2 ) );
        out = (fftw_complex*) fftw_malloc( sizeof( fftw_complex ) * ( CHUNK / 2 ) );

        if ( snapshot != NULL ) {
            int i;
            for ( i = 0; i < CHUNK / 2; i++ ) {
                in[ i ] = (double) snapshot[ i ];
            }
        }

        p = fftw_plan_dft_r2c_1d( CHUNK / 2, in, out, 0 );

        fftw_execute( p );

        fftw_destroy_plan( p );

        if ( out != NULL ) {
            int i;
            for ( i = 0; i < CHUNK / 2 / sample_spec.channels; i++ ) {
                magnitude[ i ] = (double) sqrt( pow( out[ i ][ 0 ], 2 ) + pow( out[ i ][ 1 ], 2 ) ) / (double) fft_max[ i ];
                if ( magnitude[ i ] > 1.0 ) magnitude[ i ] = 1.0;
            }
        }

        free( in );
        fftw_free(out);
    }

    return magnitude; // PyString_FromStringAndSize( (char *) snapshot, CHUNK );
}


void im_start ( void ) {

    // Pulseaudio
    int r;
    char *server = NULL;

    client_name = pa_xstrdup( "cimpulse" );
    stream_name = pa_xstrdup( "cimpulse" );

    // Set up a new main loop

    if ( ! ( mainloop = pa_threaded_mainloop_new( ) ) ) {
        fprintf( stderr, "pa_mainloop_new() failed.\n" );
        return;
    }

    mainloop_api = pa_threaded_mainloop_get_api( mainloop );

    r = pa_signal_init( mainloop_api );
    assert( r == 0 );

    /*if (!(stdio_event = mainloop_api->io_new(mainloop_api,
                                             STDOUT_FILENO,
                                             PA_IO_EVENT_OUTPUT,
                                             stdout_callback, NULL))) {
        fprintf(stderr, "io_new() failed.\n");
        goto quit;
    }
    
    // create a new connection context
    if ( ! ( context = pa_context_new( mainloop_api, client_name ) ) ) {
        fprintf( stderr, "pa_context_new() failed.\n" );
        return;
    }

    pa_context_set_state_callback( context, context_state_callback, NULL );

    /* Connect the context */
    pa_context_connect( context, server, 0, NULL );

    // pulseaudio thread
    pa_threaded_mainloop_start( mainloop );

    return;
}


```and I compiled the impulse.c with this command :
```
gcc -o Impulse.so -shared Impulse.c
```whitout errors

BUT, when I run my conky 
```
conky -c conkyrc
```I get this error :

Conky: llua_do_call: function conky_main3 execution failed: error loading module 'Impulse' from file './Impulse.so':
    ./Impulse.so: undefined symbol: pa_xstrdup

all pulseaudio variables are not recognized !

So, as I don't know nothing in C, what do you think about this error ?

Thanks!

---

### Post by ianimal on 2010-02-19
Wlourf,

As the creator of Impulse let me explain the source structure. **impulse.so** is the python bindings for the **libimpulse.so** library. Impulse.h, Impulse.c are the source code files for libimpulse.so, not impulse.so. The source code for impulse.so is impulsemodule.c. impulse.so uses the library libimpulse.so. You should not add any Lua code to Impulse.h or Impulse.c. Instead you should create a new file and follow the structure of impulsemodule.c to create a lua version using the lua c api, like the link you sent me here [http://www.wellho.net/mouth/1844_Calling-functions-in-C-from-your-Lua-script-a-first-HowTo.html](http://www.wellho.net/mouth/1844_Calling-functions-in-C-from-your-Lua-script-a-first-HowTo.html).

To build libimpulse.so use something like the following:
```

gcc -pthread -Wall -fPIC -c Impulse.c -o libimpulse.o
gcc -pthread -lpulse -lfftw3 -shared -Wl,-soname,libimpulse.so -fPIC libimpulse.o -o libimpulse.so
rm *.o

```

To build impulse.so (the python bindings) use something like the following:
```

gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.6 -c impulsemodule.c -o impulse.o
gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions -L. -limpulse -Wl,-rpath,. impulse.o -o impulse.so
rm *.o

```
*Note: -Wl,-rpath,. just allows for the dynamic linker to search for libraries in the current local path. You can also just move libimpulse.so to /usr/lib and remove -Wl,-rpath,. from the build command.

I hope this helps as a jumping off point.

---

### Post by wlourf on 2010-02-19
Thanks Ian,
That seems to be toooooooo complicated for me actually ...
I will return to my little drawnings and stay with the python stuff for the moment !


Edit 28 Feb 2010 :
With the help of Ian, I made a nice conky for his Impulse library, it's on this [post]("http://ubuntuforums.org/showpost.php?p=8861782&postcount=175").

---

### Post by olgmen on 2010-02-28
Hello everyone

I olgmen from Russia

Sorry for the mistakes, I do not know much English language and writing with an electronic translator.

I wrote a small script printed to the window conky expanding inscription MAIL. But I do not know how to connect the test mail. If a script to insert checks with conkyEmail, it is continuous, constant checking email

Text of script

```
--[[ Conky Widgets by olgmen (2010)

This widget displays the window conky expanding inscription MAIL!!!

lua_load ~/scripts/text_mail.lua
lua_draw_hook_pre widgets

]]


require 'cairo'

function text()

        local x = 0
        local y = 200
        local w=conky_window.width
        local h = 50

        local extents = cairo_text_extents_t:create()
-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1096;&#1088;&#1080;&#1092;&#1090;

        cairo_select_font_face(cr, "PT Sans", CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_BOLD)

-- font size

        size = 10

        alpha = 0.6

        local updates=conky_parse('${updates}')

        if updates == nil then updates = 0 end

            update_num=tonumber(updates)

                if (update_num % 6 == 0) then
                
                    if updates_num == nil then updates_num = 0 end

                    reset_num=update_num
        
                end

                if (reset_num >0)then

                    timer_num=update_num-reset_num

                    cairo_set_font_size(cr, size*timer_num)
                    cairo_text_extents(cr, "MAIL !!!", extents)
                    cairo_set_source_rgba(cr, 1, 0, 0, alpha+timer_num/10)
                    cairo_move_to(cr, x + w/2 - extents.x_advance/2, y + 0.5*h - extents.y_bearing/2)
                    cairo_show_text(cr, "MAIL !!!")

                end
end

    function conky_widgets()
        if conky_window == nil then return end
        local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)

    cr = cairo_create (cs)
    text()
    cairo_destroy (cr)

end

```how to make check-mail

Thank
and good day

---

### Post by wlourf on 2010-03-01
> **olgmen said:**
> how to make check-mail

Thank
and good day

hello olgmen, I don't use this function but did you try fetchmail , the documentation says :
>              **                 mails             **             (mailbox)             (interval)         Mail count in the specified mailbox or your mail         spool if not. Both mbox and maildir type mailboxes are         supported. You can use a program like fetchmail to get         mails from some server using your favourite protocol. See         also new_mails.          

aybe this like is more sure (conkyEmail) : [http://conky.linux-hardcore.com/?page_id=846](http://conky.linux-hardcore.com/?page_id=846)

---

### Post by wlourf on 2010-03-01
Hi!

When we call a conkyrc with an alsolute path like this :
```
conky -c /home/wlourf/scripts/conkyrc
```How can we get the path of the conky, or the path of a Lua script called by the conky.
It's for the audio [analyser]("http://ubuntuforums.org/showpost.php?p=8861782&postcount=175") widget, it works fine when it is called from conkyrc's path but not when called from an another path because the Lua runs python like this :
```
impulse_pipe = io.popen('python impulse.py ' .. fft , "r")
``` and doesn't find impulse.py

Thanks

---

### Post by dk75 on 2010-03-03
> **wlourf said:**
> Hi!

When we call a conkyrc with an alsolute path like this :
```
conky -c /home/wlourf/scripts/conkyrc
```How can we get the path of the conky, or the path of a Lua script called by the conky.
It's for the audio [analyser]("http://ubuntuforums.org/showpost.php?p=8861782&postcount=175") widget, it works fine when it is called from conkyrc's path but not when called from an another path because the Lua runs python like this :
```
impulse_pipe = io.popen('python impulse.py ' .. fft , "r")
``` and doesn't find impulse.py

Thanks



I don't know the proper way but I do know some improper way :twisted:

First of all, there is some better way to call external command (I found it durring "lua wait command" search):
```

function os.capture(cmd, raw)
	local f = assert(io.popen(cmd, 'r'))
	local s = assert(f:read('*a'))
	f:close()
	if raw then return s end
	s = string.gsub(s, '^%s+', '')
	s = string.gsub(s, '%s+$', '')
	s = string.gsub(s, '[\n\r]+', ' ')
	return s
end

```



and then, the improper way - test it:

conkyrc
```

background no
update_interval 1
total_run_times 1
own_window yes
own_window_type override
own_window_transparent yes
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 0 0
maximum_width 0
imlib_cache_size 0
lua_load $HOME/.conky/lua/test04.lua
lua_draw_hook_pre conky_main
TEXT

```

test04.lua
```

do

function os.capture(cmd, raw)
	local f = assert(io.popen(cmd, 'r'))
	local s = assert(f:read('*a'))
	f:close()
	if raw then return s end
	s = string.gsub(s, '^%s+', '')
	s = string.gsub(s, '%s+$', '')
	s = string.gsub(s, '[\n\r]+', ' ')
	return s
end

lua_script_dir = os.capture('find ~ -depth -mount -nowarn -name test04.lua -type f -print -quit 2>/dev/null |awk -F"/" \'{gsub($NF,"");print}\'')

impulse_command = os.capture('find ~ -depth -mount -nowarn -name impulse.py -type f -print -quit 2>/dev/null')

fft = 'you must define it here'

function conky_main()
	impulse_pipe = os.capture('python ' .. impulse_command .. ' ' .. fft)
	print (lua_script_dir)
	print (impulse_pipe)
end

end

```

---

### Post by wlourf on 2010-03-04
> **dk75 said:**
> I don't know the proper way but I do know some improper way :twisted:

First of all, there is some better way to call external command (I found it durring "lua wait command" search):
```

function os.capture(cmd, raw)
    local f = assert(io.popen(cmd, 'r'))
    local s = assert(f:read('*a'))
    f:close()
    if raw then return s end
    s = string.gsub(s, '^%s+', '')
    s = string.gsub(s, '%s+$', '')
    s = string.gsub(s, '[\n\r]+', ' ')
    return s
end

```and then, the improper way - test it:

conkyrc
```

background no
update_interval 1
total_run_times 1
own_window yes
own_window_type override
own_window_transparent yes
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 0 0
maximum_width 0
imlib_cache_size 0
lua_load $HOME/.conky/lua/test04.lua
lua_draw_hook_pre conky_main
TEXT

```test04.lua
```

do

function os.capture(cmd, raw)
    local f = assert(io.popen(cmd, 'r'))
    local s = assert(f:read('*a'))
    f:close()
    if raw then return s end
    s = string.gsub(s, '^%s+', '')
    s = string.gsub(s, '%s+$', '')
    s = string.gsub(s, '[\n\r]+', ' ')
    return s
end

lua_script_dir = os.capture('find ~ -depth -mount -nowarn -name test04.lua -type f -print -quit 2>/dev/null |awk -F"/" \'{gsub($NF,"");print}\'')

impulse_command = os.capture('find ~ -depth -mount -nowarn -name impulse.py -type f -print -quit 2>/dev/null')

fft = 'you must define it here'

function conky_main()
    impulse_pipe = os.capture('python ' .. impulse_command .. ' ' .. fft)
    print (lua_script_dir)
    print (impulse_pipe)
end

end

```
Hmmpf, that's nice ! I finally found another (proper?) way to find the script's path using conky_config from Lua API, and I didn't managed to get the path with your script :-(
```
function conky_main()

    local s=conky_config
    local pos=(s:reverse(s)):find("/")
    if pos==nil then pos=0 end
    
    lua_script_dir= s:sub(1 ,#s-pos+1)
    print (lua_script_dir)
    fft = 1
    if impulse_pipe == nil then
        --impulse_pipe = io.popen('python ' .. lua_script_dir .. 'impulse.py ' .. fft , "r")
        impulse_pipe = os.capture('python ' .. lua_script_dir .. 'impulse.py ' .. ' ' .. fft)
    end 
    
end
```Anyway, it works BUT not, it doesn't work!

Impulse.py is called, yes, but the python script needs to load the 'impulse' shared library with 
```
import impulse
```but doesn't find it because it's not in the PATH.
I can pass the path to impulse to python with an argument but after I didn't find a way to load the shared library.
I tried that for example :
```
imp.load_dynamic('impulse', os.path.join(sys.argv[2], 'impulse.so'))
```but without success, so if you have some ideas again, it will be nice !

---

### Post by dk75 on 2010-03-04
try "package.path" - I'm using it to finding lua scripts for "require" tought

```
package.path = '/usr/lib/python2.6/lib/?.so'
import impulse
```
(or whatever path to "impulse.so" is)

---

### Post by wlourf on 2010-03-04
That's working fine but ... it looks like the line 
```
local impulse =  impulse_pipe:read()
``` has no more effect, the read statement reads nothing, it's too late for me for the moment, I will check that tomorrow ...

---

### Post by dk75 on 2010-03-05
the thing is that when using **os.capture** function, string is already parsed and formated so it is already like **local impuse** not an **impulse_pipe**

You can ommit parsing by adding "raw" as parameter
```
impulse_pipe = os.capture('python ' .. lua_script_dir .. 'impulse.py ' .. ' ' .. fft, raw)
```

---

### Post by vickoxy on 2010-03-06
Hallo,
i have one problem-found clock_lua and add that lines to my conkyrc (before that shades). When i put those lines in conky i can not achieve shadows and clock at the same time. Or i have clock/or i have shades (if i remove clock lines-shades are working normally:

```
lua_load ~/scripts/draw_bg.lua
lua_draw_hook_pre draw_bg
lua_load ~/scripts/clock.lua
lua_draw_hook_pre draw_clock
```

Any idea?

---

### Post by dk75 on 2010-03-06
[http://ubuntuforums.org/showpost.php?p=8924286&postcount=12195](http://ubuntuforums.org/showpost.php?p=8924286&postcount=12195)

---

### Post by dk75 on 2010-03-06
> **vickoxy said:**
> Well-i understand only the first part-but have no idea how to merge two scripts, and what should be output for my conky (i tried to paste clock script to draw_bg-but nothing)
[..]
Could you be more specific (what to include/how in what)?

Thanks

isn't that from londonali's widgets? because I don't see main **"do .. end"** clause

ok, merged
```

do 

require 'cairo'

cs, cr, w, h = nil

function conky_cairo_window_hook()
	if conky_window == nil then return end
	if cs == nil or cairo_xlib_surface_get_width(cs) ~= conky_window.width or cairo_xlib_surface_get_height(cs) ~= conky_window.height then
		if cs then cairo_surface_destroy(cs) end
		cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	end
	if cr then cairo_destroy(cr) end
	cr = cairo_create(cs)
	w, h = conky_window.width, conky_window.height
end

function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
 
function conky_draw_bg()

	-- Settings
	
	local bg_corner_r = 25
	local bg_colour = 0xffffff
	local bg_alpha = 0.06
	
	-- End settings

	cairo_move_to(cr,bg_corner_r,0)
	cairo_line_to(cr,w-bg_corner_r,0)
	cairo_curve_to(cr,w,0,w,0,w,bg_corner_r)
	cairo_line_to(cr,w,h-bg_corner_r)
	cairo_curve_to(cr,w,h,w,h,w-bg_corner_r,h)
	cairo_line_to(cr,bg_corner_r,h)
	cairo_curve_to(cr,0,h,0,h,0,h-bg_corner_r)
	cairo_line_to(cr,0,bg_corner_r)
	cairo_curve_to(cr,0,0,0,0,bg_corner_r,0)
	cairo_close_path(cr)
 
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
	cairo_fill(cr)
end

function conky_draw_clock()
		
		-- Settings
		
		local clock_r=25
		local xc=w/6
		local yc=h/9
		local shadow_width=5
		local shadow_xoffset=0
		local shadow_yoffset=2
		local show_seconds=true
		
		-- End settings
	
	local hours=os.date("%I")
	local mins=os.date("%M")
	local secs=os.date("%S")
	
	local secs_arc=(2*math.pi/60)*secs
	local mins_arc=(2*math.pi/60)*mins
	local hours_arc=(2*math.pi/12)*hours+mins_arc/12
	
	-- Drop shadow
	
	local ds_pat=cairo_pattern_create_radial(xc+shadow_xoffset,yc+shadow_yoffset,clock_r*1.25,xc+shadow_xoffset,yc+shadow_yoffset,clock_r*1.25+shadow_width)
	cairo_pattern_add_color_stop_rgba(ds_pat,0,0,0,0,0.2)
	cairo_pattern_add_color_stop_rgba(ds_pat,1,0,0,0,0)
	
	cairo_move_to(cr,0,0)
	cairo_line_to(cr,w,0)
	cairo_line_to(cr,w,h)
	cairo_line_to(cr,0,h)
	cairo_new_sub_path(cr)
	cairo_arc(cr,xc,yc,clock_r*1.25,0,2*math.pi)
	cairo_set_source(cr,ds_pat)
	cairo_set_fill_rule(cr,CAIRO_FILL_RULE_EVEN_ODD)
	cairo_fill(cr)
	
	-- Glassy border
	
	cairo_arc(cr,xc,yc,clock_r*1.25,0,2*math.pi)
	cairo_set_source_rgba(cr,0.5,0.5,0.5,0.2)
	cairo_set_line_width(cr,1)
	cairo_stroke(cr)
	
	local border_pat=cairo_pattern_create_linear(xc,yc-clock_r*1.25,xc,yc+clock_r*1.25)
	
	cairo_pattern_add_color_stop_rgba(border_pat,0,1,1,1,0.7)
	cairo_pattern_add_color_stop_rgba(border_pat,0.3,1,1,1,0)
	cairo_pattern_add_color_stop_rgba(border_pat,0.5,1,1,1,0)
	cairo_pattern_add_color_stop_rgba(border_pat,0.7,1,1,1,0)
	cairo_pattern_add_color_stop_rgba(border_pat,1,1,1,1,0.7)
	cairo_set_source(cr,border_pat)
	cairo_arc(cr,xc,yc,clock_r*1.125,0,2*math.pi)
	cairo_close_path(cr)
	cairo_set_line_width(cr,clock_r*0.25)
	cairo_stroke(cr)
	
	-- Set clock face
	
	cairo_arc(cr,xc,yc,clock_r,0,2*math.pi)
	cairo_close_path(cr)
	
	local face_pat=cairo_pattern_create_radial(xc,yc-clock_r*0.75,0,xc,yc,clock_r)
	
	cairo_pattern_add_color_stop_rgba(face_pat,0,1,1,1,0.9)
	cairo_pattern_add_color_stop_rgba(face_pat,0.5,1,1,1,0.9)
	cairo_pattern_add_color_stop_rgba(face_pat,1,0.9,0.9,0.9,0.9)
	cairo_set_source(cr,face_pat)
	cairo_fill_preserve(cr)
	cairo_set_source_rgba(cr,0.5,0.5,0.5,0.2)
	cairo_set_line_width(cr, 1)
	cairo_stroke (cr)
	
	-- Draw hour hand
	
	local xh=xc+0.7*clock_r*math.sin(hours_arc)
	local yh=yc-0.7*clock_r*math.cos(hours_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xh,yh)
	
	cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
	cairo_set_line_width(cr,5)
	cairo_set_source_rgba(cr,0,0,0,0.5)
	cairo_stroke(cr)
	
	-- Draw minute hand
	
	local xm=xc+0.9*clock_r*math.sin(mins_arc)
	local ym=yc-0.9*clock_r*math.cos(mins_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xm,ym)
	
	cairo_set_line_width(cr,3)
	cairo_stroke(cr)
	
	-- Draw seconds hand
	
	if show_seconds then
		local xs=xc+0.9*clock_r*math.sin(secs_arc)
		local ys=yc-0.9*clock_r*math.cos(secs_arc)
		cairo_move_to(cr,xc,yc)
		cairo_line_to(cr,xs,ys)
	
		cairo_set_line_width(cr,1)
		cairo_stroke(cr)
	end
end

function conky_main()
	conky_cairo_window_hook()
	if conky_window == nil then return end
	conky_draw_bg()
	conky_draw_clock()
end

end

```

---

### Post by vickoxy on 2010-03-06
Ok, i copied that lines to my draw_bg.lua and saved it-but conky won´t show up any more.

Or should i do something else.

I downloaded scripts from londonali (conky hardcore and deviantart)

---

### Post by dk75 on 2010-03-06
then in conkyrc you load it by
```

lua_load ~/scripts/draw_bg.lua
lua_draw_hook_pre conky_main

```

basics

---

### Post by vickoxy on 2010-03-06
Thanks-that was it-now i can go on adjusting conky...:popcorn:

---

### Post by wlourf on 2010-03-06
thanks dk75, you're marvelous.
I mixed all yours ideas and now can run my conky from an absolute path with :
```
conky -c /my/path/conkyrc 
```the conkyrc need to load the Lua script with full path :
```
lua_load  $HOME/scripts/audio_spectrum1.2/audio_spectrum.lua
```the lua script needs to call the python script with the full path :
```
    if impulse_pipe == nil then
        local s=conky_config
        local pos=(s:reverse(s)):find("/")
        if pos==nil then pos=0 end
        lua_script_dir= s:sub(1 ,#s-pos+1)

        impulse_pipe = io.popen('python ' .. lua_script_dir .. 'impulse.py ' .. fft .. ' ' .. lua_script_dir, "r")
    end

```Here, I am not sure if it's better to use io.popen or os.capture (os.capture sounds more compliacted for me)
Finally, the python received the full path as second argument and use os.chdir before calling the shared library:
```
        os.chdir(sys.argv[2])
        import  impulse

```Well, this is maybe not a proper way to do it but it works, if you have any comments about that, you're welcome !

---

### Post by vickoxy on 2010-03-06
Back again (although i do not know if this is lua setup):

i saw by londonali1010 these calendar icon with date and month:
[http://londonali1010.deviantart.com/art/Conky-Config-050110-149451918](http://londonali1010.deviantart.com/art/Conky-Config-050110-149451918)

And, of course, i would love to have something like this. So, the question is: How? ;)

---

### Post by dk75 on 2010-03-06
did you read this page that you linked? ali stated that it is her "new calendar page widget".
Search for her newest widget package.

---

### Post by vickoxy on 2010-03-06
Yes-sorry-i saw it later-need conky 1.8 rc1 to run it. I do not know how to install from source, so i will just wait for regular update.

Thanks

---

### Post by wlourf on 2010-03-12
Hi all,

I use some tansformations to draw eclipses in a Lua script :
```
    cairo_translate(cr,xl,yl)
    cairo_scale(cr,10,20)
    cairo_arc(cr,0,0,1,0,2*math.pi)
    cairo_fill(cr)

```After that, I want to restore my cairo with no translation and no scaling with
```
    cairo_restore(cr)
```but it doesn't work, any ideas ?

thanks

wlourf

Edit : I found the answer : before doing transformation, we have to use :
```
cairo_save(cr)
```

---

### Post by wlourf on 2010-03-26
Hi all,

I would like to know all the  mounted drives on my computer, I can do this with :
```
local mounts = system ('mount > /tmp/mounts')
``` but is there a better way to do that ? Is it possible to write the mounted drives directly into the mounts variable ?

Thanks

Edit :
I use this script and it works fine in my [pie chart widget]("http://ubuntuforums.org/showpost.php?p=9118129&postcount=253") :
```
function read_df(file_tmp,show_media,sort_table)
    --read output of command df and return arrays of value for files systems
    --reurn array of table {file syst, occupied space , total space , convert to G, M, K ...}
    local mounts = os.execute ('df > ' .. file_tmp)
    if mounts ~= 0 then
        print ("Error with df command, exit")
        return nil
    end
    
    local file = io.open(file_tmp,"r")
    if file==nil then
        print ("Error while reading " .. file_tmp .. ", exit")
        return nil
    end

    local results={}
    while true do
         local line = file:read("*l")
         if line == nil then break end
         while string.match(line,"  ") do
             line=string.gsub(line,"  "," ")
         end
        local arr_l=string.split(line," ")
        local match = string.match(arr_l[1],"/")
        
        if string.match(arr_l[1],"/") then
            if not show_media then arr_l[6]=string.gsub(arr_l[6],"/media/","",1) end
            table.insert(results,{arr_l[6],arr_l[3]*1024,arr_l[2]*1024,true})
        end
    end

    io.close()
    
    if sort_table then
        --how to sort table into table?
        local flagS=true
        while flagS do
            for k=2, #results do 
                flagS=false
                if tonumber(results[1][3])>tonumber(results[2][3]) then
                    local tmpV = results[1]
                    results[1] = results[2]
                    results[2] = tmpV
                    flagS=true
                end
                if tonumber(results[k][3])<tonumber(results[k-1][3]) then
                    local tmpV = results[k-1]
                    results[k-1] = results[k]
                    results[k] = tmpV
                    flagS=true
                end
            end
        end
    end
    
    return results --array {file syst, occupied space , total space }
end

```

---

### Post by wlourf on 2010-04-17
How to use **cairo_set_operator(cr,CAIRO_OPERATOR_CLEAR)** in Lua?
I am running the first example of this page : [http://www.cairographics.org/operators/](http://www.cairographics.org/operators/)
Drawing a first red rectangle and drawing a second one which will clear the first one.
The resulting image should be :
[IMG]http://www.cairographics.org/operators/clear.png[/IMG]
but in my case the second rectangle is BLACK.

The function used is :
```
function conky_main()
--http://cairographics.org/operators/
    if conky_window==nil then return end
    local w,h =conky_window.width, conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    
    --local cs = cairo_image_surface_create(CAIRO_FORMAT_ARGB32, w, h)

    local cr=cairo_create(cs)
    
    cairo_rectangle (cr, 0, 0, 120, 90);
    cairo_set_source_rgba (cr, 0.7, 0, 0, 0.8);
    cairo_fill (cr);
    cairo_set_operator(cr,CAIRO_OPERATOR_CLEAR)
    cairo_rectangle (cr, 40, 30, 120, 90);
    cairo_set_source_rgba (cr, 0, 0, 0.9, 0.4);
    cairo_fill (cr);

    cairo_destroy(cr)
end
```I suspect I have to create a transparent surface but how ? If I use :
**local cs = cairo_image_surface_create(CAIRO_FORMAT_ARGB32, w, h)** and save it as PNG file, the CLEAR OPEAROR will be OK. 
So, the big question is : Is there a way to create a xlib transparent surface ?

Thanks !

---

### Post by dk75 on 2010-04-18
It works for me.

```
conky -v
Conky 1.8.0_rc2 compiled Sat Mar 13 20:54:18 CET 2010 for Linux 2.6.32-15-generic (x86_64)

Compiled in features:

System config file: /usr/local/etc/conky/conky.conf
Package library path: /usr/local/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * nvidia
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2
```

```
do 

require 'cairo'

cs, cr = nil
 
function conky_main()
	if conky_window == nil then return end
	if cs == nil or cairo_xlib_surface_get_width(cs) ~= conky_window.width or cairo_xlib_surface_get_height(cs) ~= conky_window.height then
		if cs then cairo_surface_destroy(cs) end
		cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	end
	if cr then cairo_destroy(cr) end
	cr = cairo_create(cs)
    
	cairo_rectangle (cr, 0, 0, 120, 90)
	cairo_set_source_rgba (cr, 0.7, 0, 0, 0.8)
	cairo_fill (cr)
	cairo_set_operator(cr,CAIRO_OPERATOR_CLEAR)
	cairo_rectangle (cr, 40, 30, 120, 90)
	--cairo_set_source_rgba (cr, 0, 0, 0.9, 0.4)
	cairo_fill (cr)

end

end
```

---

### Post by wlourf on 2010-04-18
Hi dk75,

I have almost the same version of conky, can you post your conkyrc please, I think there is a problem with the settings I use. Thanks.
Edit : I run conky v 1.8.0 (not rc2) and have not ALSA mixer support.

---

### Post by dk75 on 2010-04-18
```
background no
update_interval 1
total_run_times 0
own_window yes
own_window_type normal
own_window_argb_visual yes
own_window_transparent yes
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_class Conky
#double_buffer yes
gap_x 50
gap_y 50
border_inner_margin 0
border_outer_margin 0
minimum_size 200 200
maximum_width 200
imlib_cache_size 0
lua_load $HOME/.conky/lua/test06.lua
lua_draw_hook_pre conky_main
TEXT
```



> **wlourf said:**
> Edit : I run conky v 1.8.0 (not rc2) and have not ALSA mixer support.

OK. So I've compiled this same as you
```
conky -v
Conky 1.8.0 compiled Sun Apr 18 16:19:45 CEST 2010 for Linux 2.6.32-18-generic (x86_64)

Compiled in features:

System config file: /usr/local/etc/conky/conky.conf
Package library path: /usr/local/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * wireless
  * nvidia
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2
```


My configure line
```
./configure --enable-curl --enable-rss --enable-imlib2 --enable-lua-imlib2 --enable-lua-cairo --enable-wlan --enable-nvidia
```

---

### Post by wlourf on 2010-04-18
> **dk75 said:**
> ```
background no
update_interval 1
total_run_times 0
own_window yes
own_window_type normal
own_window_argb_visual yes
own_window_transparent yes
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_class Conky
#double_buffer yes
gap_x 50
gap_y 50
border_inner_margin 0
border_outer_margin 0
minimum_size 200 200
maximum_width 200
imlib_cache_size 0
lua_load $HOME/.conky/lua/test06.lua
lua_draw_hook_pre conky_main
TEXT
```OK. So I've compiled this same as you
```
conky -v
Conky 1.8.0 compiled Sun Apr 18 16:19:45 CEST 2010 for Linux 2.6.32-18-generic (x86_64)

Compiled in features:

System config file: /usr/local/etc/conky/conky.conf
Package library path: /usr/local/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * wireless
  * nvidia
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2
```My configure line
```
./configure --enable-curl --enable-rss --enable-imlib2 --enable-lua-imlib2 --enable-lua-cairo --enable-wlan --enable-nvidia
```

For the transparency, it works now but only in Gnome. I made two big mistakes :
1. I forgot the [B]own_window_argb_visual yes
[/B]2. I ran my conkyrc with Openbox and there is no transparency with Openbox : to have transparancy with openbox, I had to install xcompmgr and transet and everything is OK.

You're lucky for the compilation, you have Alsa Mixer. As I don't really need it, I won't look forward for it.

Edit : I managed to do something intersting with this cairo's Operator :
_[[IMG]http://pix.toile-libre.org/upload/thumb/1271695935.png[/IMG]]("http://pix.toile-libre.org/?img=1271695935.png")_
Full script in conky mega-thread : [http://ubuntuforums.org/showpost.php?p=9145982&postcount=12461](http://ubuntuforums.org/showpost.php?p=9145982&postcount=12461)
Thanks again for your help dk75 !

---

### Post by wlourf on 2010-04-28
(sorry double post)

---

### Post by wlourf on 2010-04-28
Hello again :P

A new problem with Conky/Lua if someone can help me, I would like to pass arguments with spaces from conky to Lua, is it possible ?
```
lua_draw_hook_post main_function arg1 "arg2 arg2bis"
```Above I think I have 2 arguments but the Lua script sees 3 arguments :
```
arg1
"arg2
arg3"
```If not possible, I will use characters like "underscore" instead of spaces and remove them in the Lua script.

Thanks

---

### Post by Zookalicious on 2010-05-26
Hey all, I'm going slightly insane here. I'm pretty sure I'm following all of the directions right, but I am having zero luck at getting the combination clock_rings script to work. 

Basically nothing shows up. I read through this entire thread, and have been looking this up for a few days now, but no success... If anyone could help me out here I would really appreciate it. 

```

Conky 1.8.0 compiled Fri Apr 23 10:42:08 UTC 2010 for Linux 2.6.24-27-server (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2


```Here's my .conkyrc

```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat connections to your computer
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft no

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 250 5

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

    # Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

text_buffer_size 2048

# Gap between borders of screen and text
gap_x 20
gap_y 20

#Clock Script
lua_load ~/clock.lua
lua_draw_hook_pre clock_rings

# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color
${color purple}SYSTEM ${hr 2}$color
Ubuntu 10.04 Lucid Lynx 
Linux $kernel on $machine

${color purple}CPU ${hr 2}$color
${freq}MHz Load: ${loadavg} Temp: ${nvidia temp}&#730;C
$cpubar
NAME              PID     CPU%   MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color purple}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color

Ubuntu:    ${fs_used_perc /}% ${fs_bar 6 /}$color
Macintosh: ${fs_used_perc /media/sda2}% ${fs_bar 6 /media/sda2}$color
Windows:   ${fs_used_perc /host}% ${fs_bar 6 /host}

${color purple}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1}/s ${alignr}Up: ${upspeed eth1}/s
${downspeedgraph eth1 25,140 000000 ffffff} ${alignr}${upspeedgraph eth1
25,140 000000 ffffff}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

#Weather script
${color purple}WEATHER ${hr 2}$color
${execpi 1800 conkyForecast --location=CAXX0043 --template=/usr/share/conkyforecast/example/conkyForecast.template}
#
#Rhythmbox script
${color purple}NOW PLAYING ${hr 2}$color

${color purple}${execp conkyRhythmbox --template=/usr/share/conkyrhythmbox/example/conkyRhythmbox.template}
${execibar 1 conkyRhythmbox --datatype=PP}

```Aaaaaaaand the script is the same as the v. 1.1.1. that was downloaded from here: [http://conky.linux-hardcore.com/?page_id=2869](http://conky.linux-hardcore.com/?page_id=2869)

Also my screenshot. 
[[IMG]http://www.freeimagehosting.net/uploads/1b24e8380e.png[/IMG]]("http://www.freeimagehosting.net/")

---

### Post by bra|10n on 2010-05-26
I'll try to help...

I can see you calling up the script in your conkyrc, so I ask you where exactly did you save the script?

---

### Post by wlourf on 2010-05-26
> **Zookalicious said:**
> Hey all, I'm going slightly insane here. I'm pretty sure I'm following all of the directions right, but I am having zero luck at getting the combination clock_rings script to work. 

Basically nothing shows up. I read through this entire thread, and have been looking this up for a few days now, but no success... If anyone could help me out here I would really appreciate it. 


Do you have any error message when you run your conky with this kind of command :
> conky -c /full/path/your_conkyrc

---

### Post by Zookalicious on 2010-05-27
Thanks for your replies wlourf and bra|10n.

```

chris@ubuntu:~$ conky -c /home/chris/.conkyrc
Conky: desktop window (1e000a9) is subwindow of root window (15d)
Conky: window type - override
Conky: drawing to created window (0x5800001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT1/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT1/state: No such file or directory

```That's what comes up in the Terminal. I tried removing the battery sections of the script, no such luck though. 

[U][[IMG]http://www.freeimagehosting.net/uploads/th.c43443e58d.png[/IMG]]("http://www.freeimagehosting.net/image.php?c43443e58d.png")

[/U] This is a screenshot showing where I have the script located. its in /home/chris/clock.lua, which is the same place that I have it set to call (i believe???)

It seems to call up the script the way it should which leads me to believe that there isn't a mistake in the location.... and if I change the .lua it notices, but it just doesn't put anything on my screen :S

Thank you both for your interest in helping me to solve this :P I promise to return the favour when ever I can.

[Edit: screenshot was massive]

---

### Post by Zookalicious on 2010-05-27
Oh btw wlourf, I just checked out your blog and realized I actually have you favourited on Deviantart. Kinda funny.

---

### Post by bra|10n on 2010-05-27
If you're sure the script is loading then I can think of two things;
1. You are calling a variable that the script is not 'happy' with. More than likely BAT1
2. The script is in fact loaded off screen, so try load only the script without your regular conky details. 

I just remembered a little nuance I have in renaming such scripts to conky_lua. Why? is the question

---

### Post by wlourf on 2010-05-27
bra|10n is right, you have to set the center of the clock (relative to the top left corner of the conky window) in the lua script, on lines 209 :
```

clock_x=100
clock_y=100

```100 is just an example.

You can also set the conky window size with :
```
minimum_size 600 150
```Zookalicious, so it's YOU my reader ! what is your nickname on dA, internet world is small :)

---

### Post by Zookalicious on 2010-05-27
Oh lordy do I ever love you both! That was indeed the issue, I now have a lovely rendered clock on my desktop :) I'll still have to play around with the location and all but this is great!

Thank you both for your help, I really appreciate it, and btw wlourf my da account is angrypsyco. I favoured one of your conky scripts a while back and just recently +deviantwatched your da.

---

### Post by Hume's doona on 2010-05-28
I'm using a conky from here on the forums.

conkyrc
```
# -- Conky settings -- #
background no
update_interval 1
 
cpu_avg_samples 2
net_avg_samples 2
 
override_utf8_locale yes
 
double_buffer yes
no_buffers yes
 
text_buffer_size 2048
imlib_cache_size 0
 
# -- Window specifications -- #
 
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
 
border_inner_margin 0
border_outer_margin 0
 
minimum_size 320 800
maximum_width 320
 
alignment bottom_right
gap_x 0
gap_y 0
 
# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
 
# -- Text settings -- #
use_xft yes
xftfont MaiandraGD:size=24
xftalpha 0.4
 
uppercase no
 
default_color 888888
 
# -- Lua Load -- #
lua_load ~/conky/lua/lua.lua
lua_draw_hook_pre ring_stats
 
TEXT
${alignr}${voffset 53}${goto 90}${font MaiandraGD:size=11}${time %A, %d %B %Y}


${voffset 5}${goto 164}${font MaiandraGD:size=16}${time %H:%M}



${voffset -40}${goto 100}${font MaiandraGD:size=9}Kernel:${offset 70}Uptime:
${goto 90}${font MaiandraGD:size=9}$kernel${offset 40}$uptime 
${voffset 57}${goto 117}${font snap:size=8}${cpu cpu0}%
${goto 117}${cpu cpu1}%
${goto 117}CPU
${voffset 19}${goto 145}${memperc}%
${goto 145}$swapperc%
${goto 145}MEM
${voffset 25}${goto 170}${acpitemp} C
${goto 170}TEMP
${voffset 27}${goto 198}${downspeed eth0}
${goto 198}${upspeed eth0}
${goto 205}NET
${voffset 21}${goto 222}${fs_used /}
${goto 222}${fs_used /home}
${goto 230}DISK
```

lua.lua
```
--[[
Ring Meters by londonali1010 (2009)
 
This script draws percentage meters as rings. It is fully customisable; all options are described in the script.
 
IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num > 5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num > 3; conversely if you update Conky every 0.5s, you should use update_num > 10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.
 
To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
	lua_load ~/scripts/rings-v1.2.1.lua
	lua_draw_hook_pre ring_stats
 
Changelog:
+ v1.2.1 -- Fixed minor bug that caused script to crash if conky_parse() returns a nil value (20.10.2009)
+ v1.2 -- Added option for the ending angle of the rings (07.10.2009)
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]
 
settings_table = {
	{
		-- Edit this table to customise your rings.
		-- You can create more rings simply by adding more elements to settings_table.
		-- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
		name='time',
		-- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
		arg='%I.%M',
		-- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
		max=12,
		-- "bg_colour" is the colour of the base ring.
		bg_colour=0x888888,
		-- "bg_alpha" is the alpha value of the base ring.
		bg_alpha=0.3,
		-- "fg_colour" is the colour of the indicator part of the ring.
		fg_colour=0x888888,
		-- "fg_alpha" is the alpha value of the indicator part of the ring.
		fg_alpha=0.5,
		-- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
		x=191, y=145,
		-- "radius" is the radius of the ring.
		radius=32,
		-- "thickness" is the thickness of the ring, centred around the radius.
		thickness=4,
		-- "start_angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
		start_angle=0,
		-- "end_angle" is the ending angle of the ring, in degrees, clockwise from top. Value can be either positive or negative, but must be larger (e.g. more clockwise) than start_angle.
		end_angle=360
	},
	{
		name='time',
		arg='%M.%S',
		max=60,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=191, y=145,
		radius=37,
		thickness=4,
		start_angle=0,
		end_angle=360
	},
	{
		name='time',
		arg='%S',
		max=60,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=191, y=145,
		radius=42,
		thickness=4,
		start_angle=0,
		end_angle=360
	},
	{
		name='cpu',
		arg='cpu0',
		max=100,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=140, y=300,
		radius=26,
		thickness=5,
		start_angle=-90,
		end_angle=180
	},
	{
		name='cpu',
		arg='cpu1',
		max=100,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=140, y=300,
		radius=20,
		thickness=5,
		start_angle=-90,
		end_angle=180
	},
	{
		name='memperc',
		arg='',
		max=100,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=170, y=350,
		radius=26,
		thickness=5,
		start_angle=-90,
		end_angle=180
	},
	{
		name='swapperc',
		arg='',
		max=100,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=170, y=350,
		radius=20,
		thickness=5,
		start_angle=-90,
		end_angle=180
	},
	{
		name='time',
		arg='%d',
		max=31,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=191, y=145,
		radius=50,
		thickness=5,
		start_angle=-140,
		end_angle=-30
	},
	{
		name='time',
		arg='%m',
		max=12,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=191, y=145,
		radius=50,
		thickness=5,
		start_angle=30,
		end_angle=140
	},
	{
		name='fs_used_perc',
		arg='/',
		max=100,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=260, y=503,
		radius=26,
		thickness=5,
		start_angle=-90,
		end_angle=180
	},
	{
		name='fs_used_perc',
		arg='/home',
		max=100,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=260, y=503,
		radius=20,
		thickness=5,
		start_angle=-90,
		end_angle=180
	},
	{
		name='upspeedf',
		arg='eth0',
		max=50,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=230, y=452,
		radius=20,
		thickness=5,
		start_angle=-90,
		end_angle=180
	},
	{
		name='downspeedf',
		arg='eth0',
		max=100,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=230, y=452,
		radius=26,
		thickness=5,
		start_angle=-90,
		end_angle=180
	},
	{
		name='acpitemp',
		arg='',
		max=100,
		bg_colour=0x888888,
		bg_alpha=0.3,
		fg_colour=0x888888,
		fg_alpha=0.5,
		x=200, y=401,
		radius=26,
		thickness=6,
		start_angle=-90,
		end_angle=180
	},
}
 
require 'cairo'
 
function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
 
function draw_ring(cr,t,pt)
	local w,h=conky_window.width,conky_window.height
 
	local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
 
	local angle_0=sa*(2*math.pi/360)-math.pi/2
	local angle_f=ea*(2*math.pi/360)-math.pi/2
	local t_arc=t*(angle_f-angle_0)
 
	-- Draw background ring
 
	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
 
	-- Draw indicator ring
 
	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
end
 
function conky_ring_stats()
	local function setup_rings(cr,pt)
		local str=''
		local value=0
 
		str=string.format('${%s %s}',pt['name'],pt['arg'])
		str=conky_parse(str)
 
		value=tonumber(str)
		if value == nil then value = 0 end
		pct=value/pt['max']
 
		draw_ring(cr,pct,pt)
	end
 
	if conky_window==nil then return end
	local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
 
	local cr=cairo_create(cs)	
 
	local updates=conky_parse('${updates}')
	update_num=tonumber(updates)
 
	if update_num>5 then
		for i in pairs(settings_table) do
			setup_rings(cr,settings_table[i])
		end
	end
end
```

I use a 3g dongle for internet and want to measure ppp0 for days and months, in place of upspeed and downspeed. I can monitor it in a terminal, with vnstat, and I want to know how to work that into the lua rings? The text part is well documented on the web.

Thanks

---

### Post by Zookalicious on 2010-05-28
Here is what I used to measure the total amount of data uploaded / downloaded. 

```

${totaldown ppp0}
${totalup ppp0}

```

And something to display it as a ring would look something like this.... (but I'm not positive, so give it a shot)

```

[FONT=monospace]    {
        name='totalup',
        arg='ppp0',
        max=500,     <-------------------Whatever your maximum data is. 
        bg_colour=0x888888,
        bg_alpha=0.3,
        fg_colour=0x888888,
        fg_alpha=0.5,
        x=140, y=300,
        radius=20,
        thickness=5,
        start_angle=-90,
        end_angle=180
    },
[/FONT]
```

Hope that works for you :)

---

### Post by Hume's doona on 2010-05-29
> **Zookalicious said:**
> Here is what I used to measure the total amount of data uploaded / downloaded. 
<snip>
Hope that works for you :)

Thanks, that worked a charm. Will that keep a monthly record? Or reset with every reboot?

---

### Post by junoon53 on 2010-05-29
^That doesn't work for me. The ring foreground doesn't display. It only seems to work if the conky variable returns a float value.

---

### Post by renmush on 2010-05-30
Hi all, I'd like to share my cairo script with you and ask a couple of questions.

[ATTACH]158780[/ATTACH]
See it in action [here.]("http://www.youtube.com/watch?v=pJ7lc1fqw6w")

substrate.lua
```

--~ Sam Swift's implementation of substrate by Jared Tarbell in lua and 
--~ cairo for conky. 
--~ For the orginal see
--~ http://www.complexification.net/gallery/machines/substrate/
--~ For my implementation in pygame see
--~ http://www.pygame.org/project-substrate-1488-2659.html

require 'cairo'
math.randomseed(os.time()) 
first_run = true 
max_cracks = 10
dist = 0.8
radius = 180
start_pts = 3

function check_pt(x,y) -- Check if point is ok
	local ans = true
	-- Check if within bounds and not collided with different crack
	--if (w/2-x)^2 + (h/2-y)^2 >= radius^2 or grid[x][y] ~= 10 then --Circle
	if (w-x)^2 + y^2 >= radius^2 or x > w-1 or y < 2 or grid[x][y] ~= 10 then --Quarter circle
	--if x < 2 or x > w-1 or y < 2 or y > h-1 or grid[x][y] ~= 10 then --Square
		ans = false
	end
	return ans
end

function new_crack(i) -- Create new crack
	-- Find random point that is already cracked
	local n = math.random(#points)
	local nx = points[n][1]
	local ny = points[n][2]
	-- Get its angle
	local na = grid[nx][ny]
	-- Change angle by pi/2 (+- a bit)
	if math.random(2) == 2 then
		na = na + math.pi/2 + (math.random(5)-3)*math.pi/180
	else
		na = na - math.pi/2 + (math.random(5)-3)*math.pi/180
	end
	-- Either insert  at end of list or specific place
	if i == 0 then
		table.insert(a_cr,{nx,ny,na,0})
	else
		table.insert(a_cr,i,{nx,ny,na,0})
	end
end

function move(i) -- Move and draw current crack
	-- Get crack start position, angle and length
	local x,y,a,l = a_cr[i][1], a_cr[i][2], a_cr[i][3], a_cr[i][4]
	-- Get old end position
	local ox,oy = math.floor(l*math.cos(a)+x), math.floor(l*math.sin(a)+y)
	-- Get new end position
	l = l + dist
	local ex,ey = l*math.cos(a)+x, l*math.sin(a)+y
	-- Check old and new end positions are not the same (rounded down to integers)
	if ox ~= math.floor(ex) or oy ~= math.floor(ey) and l > 2 then
		--Check if new end position is ok
		if check_pt(math.floor(ex),math.floor(ey)) then
			-- Add new point to possible start (and collision) positions 
			table.insert(points,{math.floor(ex),math.floor(ey)})
			grid[math.floor(ex)][math.floor(ey)] = a
			-- Update length
			a_cr[i][4] = l
			-- Draw line
			cairo_move_to(cr,x,y) 
			cairo_line_to(cr,ex,ey)
		else
			-- Replace self with new crack
			table.remove(a_cr,i)
			new_crack(i)
			if #a_cr < max_cracks then
				new_crack(0)
			end
			-- Add to list of old cracks
			table.insert(o_cr,{x,y,ex,ey})
		end
	else
		-- Update length
		a_cr[i][4] = l
		-- Draw line
		cairo_move_to(cr,x,y)
		cairo_line_to(cr,ex,ey) 
	end
end

function draw_old(i) -- Draw old cracks
	-- Draw line
	cairo_move_to(cr,o_cr[i][1],o_cr[i][2]) 
	cairo_line_to(cr,o_cr[i][3],o_cr[i][4])
end

function conky_draw_substrate() -- Main loop
	if conky_window == nil then 
		return 
	end
	-- For some reason conky initialises to 10*10, so have ignored it
	w = 200--conky_window.width --Does not work as initially conky is small.
	h = 200--conky_window.height
	if first_run  then 
		-- Initialise surface and context
		cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
		cr = cairo_create(cs)
		cairo_set_line_width(cr,1)
		cairo_set_source_rgba(cr,0,0,0,1)
		-- Global containers for the cracks
		grid = {}
		a_cr = {}
		o_cr = {}
		points = {}
		local i, j, k = 1, 1, 1
		-- Create grid of (un)cracked points
		while i <= w do
			table.insert(grid,{})
			j = 1
			while j <= h do
				table.insert(grid[i],10)
				j=j+1
			end
			i=i+1
		end
		-- Create initial cracks
		while k <= start_pts do
			local x,y = 0,0
			while not check_pt(x,y) do
				x,y = math.random(w),math.random(h)
			end
			grid[x][y] = math.random(360)*math.pi/180
			table.insert(points,{x,y})
			new_crack(0) 
			k=k+1
		end
		first_run = false 
	end
	-- Loop through current cracks 
	for i,v in ipairs(a_cr) do
		move(i)
	end
	-- Loop through old cracks
	for i,v in ipairs(o_cr) do
		draw_old(i)
	end
	cairo_set_line_width(cr,1)
	cairo_stroke(cr) 
	-- Draw boundary
	cairo_set_line_width (cr, 4.0)
	cairo_arc (cr, w, 0, radius, math.pi/2, math.pi)
	cairo_stroke (cr);
	-- Check if time to restart
	if #o_cr > 600 then
		first_run = true 
	end
end

```

conkyrc
```

use_xft yes
update_interval 0.05
total_run_times 0
double_buffer yes
no_buffers yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_class conky
minimum_size 200 200
maximum_width 200 
use_spacer none
draw_shades no
draw_outline no
draw_borders no
alignment tr
gap_x -10
gap_y 0
default_color 000000

lua_load substrate.lua
lua_draw_hook_pre draw_substrate

TEXT
 


```

My questions are:
[LIST]
[*]Why do I need the negative gap_x to make the conky flush with the screen edge?
[*]Why is conky_window.height == 10 on the first run?
[*]Is there any way to preserve what has been drawn to a surface, thereby reducing the number of drawing (cairo_line_to()) calls I must make? 
[/LIST]

To clarify the last question:
I would like to draw my line to a surface, and the next time conky calls the script still have this line on the surface. 
This would remove the requirement of making up to 600 draw line calls each iteration for the "old cracks".
I have experimented with cairo_stroke_preserve but this is less efficient as it still retains a full list of lines to draw. 

Alternatively I would like two surfaces: an 'old' surface, with all previous drawings on it and a 'new' surface with this frame's drawings.

Any help would be greatly appreciated.
Smiles
Sam

---

### Post by wlourf on 2010-05-30
> **renmush said:**
> My questions are:
[LIST]
[*]Why do I need the negative gap_x to make the conky flush with the screen edge?
[*]Why is conky_window.height == 10 on the first run?
[*]Is there any way to preserve what has been drawn to a surface, thereby reducing the number of drawing (cairo_line_to()) calls I must make?
[/LIST]

To clarify the last question:
I would like to draw my line to a surface, and the next time conky calls the script still have this line on the surface. 
This would remove the requirement of making up to 600 draw line calls each iteration for the "old cracks".
I have experimented with cairo_stroke_preserve but this is less efficient as it still retains a full list of lines to draw. 

Alternatively I would like two surfaces: an 'old' surface, with all previous drawings on it and a 'new' surface with this frame's drawings.

Any help would be greatly appreciated.
Smiles
Sam
Hi,
For the size of the window I had the same problem, solved with :
```
    if conky_window == nil or conky_window.width < 20 then 
        return 
    end
```To preserve the drawn surface, maybe you should look to imlib, it's just an idea, I'm not sure that will work with your script  but it is what I used for my photo album on post 121 of this thread : when cracks are drawn to the surface save the surface in a file and recall this image after creating the surface ...

---

### Post by Zookalicious on 2010-05-30
> **Hume's doona said:**
> Thanks, that worked a charm. Will that keep a monthly record? Or reset with every reboot?

I'm not one hundred percent sure.. Try downloading something, then quitting conky and restarting it. See if the number goes back to zero. 

> **junoon53 said:**
>          ^That doesn't work for me. The ring foreground doesn't display. It  only seems to work if the conky variable returns a float value.     

Trying changing the alpha values. The colours just might be too close. Alternatively, you might need to replace ppp0 with eth0 or eth1 depending on what connection you're using.

---

### Post by renmush on 2010-06-02
[ATTACH]159152[/ATTACH]

Thanks a lot wlourf.

Your suggestion solved my sizing problem perfectly. 

I think I might try imlib2 when I have a little more time.

It turns out my offset problem was due to a typeo on my part.

I have now introduced an elegant fade out. 

Until I have time to optimize it I will keep it small and slow to prevent it eating cpu.

substrate.lua
```

--~ Sam Swift's implememntation of substrate by Jared Tarbell in lua and 
--~ cairo for conky. 
--~ For the orginal see
--~ http://www.complexification.net/gallery/machines/substrate/
--~ For my implementation in pygame see
--~ http://www.pygame.org/project-substrate-1488-2659.html

require 'cairo'
require 'imlib2'
math.randomseed(os.time()) 
first_run = true
max_cracks = 10
dist = 0.8
start_pts = 2

function check_pt(x,y) -- Check if point is ok
	local ans = true
	-- Check if within bounds and not collided with different crack
	if (centre[1]-x)^2 + (centre[2]-y)^2 >= radius^2 or x < 2 or x > w-1 or y < 2 or y > h-1 or grid[x][y] ~= 10 then
		ans = false
	end
	return ans
end

function new_crack(i) -- Create new crack
	-- Find random point that is already cracked
	local n = math.random(#points)
	local nx = points[n][1]
	local ny = points[n][2]
	-- Get its angle
	local na = grid[nx][ny]
	-- Change angle by pi/2 (+- a bit)
	if math.random(2) == 2 then
		na = na + math.pi/2 + (math.random(5)-3)*math.pi/180
	else
		na = na - math.pi/2 + (math.random(5)-3)*math.pi/180
	end
	-- Either insert  at end of list or specific place
	if i == 0 then
		table.insert(a_cr,{nx,ny,na,0})
	else
		table.insert(a_cr,i,{nx,ny,na,0})
	end
end

function move(i) -- Move and draw current crack
	-- Get crack start position, angle and length
	local x,y,a,l = a_cr[i][1], a_cr[i][2], a_cr[i][3], a_cr[i][4]
	-- Get old end position
	local ox,oy = math.floor(l*math.cos(a)+x), math.floor(l*math.sin(a)+y)
	-- Get new end position
	l = l + dist
	local ex,ey = l*math.cos(a)+x, l*math.sin(a)+y
	-- Check old and new end positions are not the same (rounded down to integers)
	if ox ~= math.floor(ex) or oy ~= math.floor(ey) and l > 2 then
		--Check if new end position is ok
		if check_pt(math.floor(ex),math.floor(ey)) then
			-- Add new point to possible start (and collision) positions 
			table.insert(points,{math.floor(ex),math.floor(ey)})
			grid[math.floor(ex)][math.floor(ey)] = a
			-- Update length
			a_cr[i][4] = l
			-- Draw line
			cairo_move_to(cr,x,y) 
			cairo_line_to(cr,ex,ey)
		else
			-- Replace self with new crack
			table.remove(a_cr,i)
			new_crack(i)
			if #a_cr < max_cracks then
				new_crack(0)
			end
			-- Add to list of old cracks
			table.insert(o_cr,{x,y,ex,ey})
		end
	else
		-- Update length
		a_cr[i][4] = l
		-- Draw line
		cairo_move_to(cr,x,y)
		cairo_line_to(cr,ex,ey) 
	end
end

function draw_old(i) -- Draw old cracks
	-- Draw line
	cairo_move_to(cr,o_cr[i][1],o_cr[i][2]) 
	cairo_line_to(cr,o_cr[i][3],o_cr[i][4])
end

function conky_draw_substrate(lr,col) -- Main loop
	if conky_window == nil or conky_window.width < 20 then 
		return 
	end
	if first_run then 
		w = conky_window.width 
		h = conky_window.height
		radius = w-2
		-- Initialise surface and context
		if cs then
			cairo_surface_finish(cs)
		end
		cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
		cr = cairo_create(cs)
		faden = 1
		if lr == "l" then 
			centre = {0,0}
		else
			centre = {w,0}
		end
		-- Global containers for the cracks 
		grid = {}
		a_cr = {}
		o_cr = {}
		points = {}
		local i, j, k = 1, 1, 1
		-- Create grid of (un)cracked points
		while i <= w do
			table.insert(grid,{})
			j = 1
			while j <= h do
				table.insert(grid[i],10)
				j=j+1
			end
			i=i+1
		end
		-- Create initial cracks
		while k <= start_pts do
			local x,y = 999,999
			while not check_pt(x,y) do
				x,y = math.random(w),math.random(h)
			end
			grid[x][y] = math.random(360)*math.pi/180
			table.insert(points,{x,y})
			new_crack(0) 
			k=k+1
		end
		first_run = false
	end
	-- Loop through current cracks 
	for i,v in ipairs(a_cr) do
		move(i)
	end
	-- Loop through old cracks
	for i,v in ipairs(o_cr) do
		draw_old(i)
	end
	-- Fade out gracefully
	if col == "b" then
		cairo_set_source_rgba(cr,0,0,0,(51-faden)/50)
	else
		cairo_set_source_rgba(cr,1,1,1,(51-faden)/50)
	end
	cairo_set_line_width(cr,1)
	cairo_stroke(cr) 
	-- Draw boundary
	if col == "b" then
		cairo_set_source_rgba(cr,0,0,0,1)
	else
		cairo_set_source_rgba(cr,1,1,1,1)
	end
	cairo_set_line_width (cr, 3.0) 
	cairo_arc (cr, centre[1], centre[2], radius, 0, 2*math.pi)
	cairo_stroke (cr)
	-- Check if time to restart
	if #o_cr > 500 then
		faden = faden + 1
	end
	if faden >= 50 then 
		faden = 1
		first_run = true 
	end
end

```

conkyrc
```

use_xft yes
update_interval 0.1
total_run_times 0
double_buffer yes
no_buffers yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_class conky
minimum_size 182 182
maximum_width 182
use_spacer none
draw_shades no
draw_outline no
draw_borders no
alignment tr
gap_x 0
gap_y 0
default_color 000000

lua_load substrate.lua
lua_draw_hook_pre draw_substrate r b

TEXT
 


```

Smiles

---

### Post by Scooter_X on 2010-06-04
Hey, wondering if someone could help me with this strange problem. When I try to draw a line or text in my lua script, I get what you see in the screenshot. Lines dragging from my rings to my text/line. I just don't know why. I'm no programmer, so it's likely something simple but I wanted someone else to take a peek at my script:

```
--[[
Ring Meters by londonali1010 (2009)
 
This script draws percentage meters as rings. It is fully customisable; all options are described in the script.
 
IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num > 5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num > 3; conversely if you update Conky every 0.5s, you should use update_num > 10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.
 
To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/rings-v1.2.1.lua
    lua_draw_hook_pre ring_stats
 
Changelog:
+ v1.2.1 -- Fixed minor bug that caused script to crash if conky_parse() returns a nil value (20.10.2009)
+ v1.2 -- Added option for the ending angle of the rings (07.10.2009)
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]
 
settings_table = {
--[[
    {
        -- Edit this table to customise your rings.
        -- You can create more rings simply by adding more elements to settings_table.
        -- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
        name='time',
        -- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
        arg='%I.%M',
        -- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
        max=12,
        -- "bg_colour" is the colour of the base ring.
        bg_colour=0xffffff,
        -- "bg_alpha" is the alpha value of the base ring.
        bg_alpha=0.1,
        -- "fg_colour" is the colour of the indicator part of the ring.
        fg_colour=0xffffff,
        -- "fg_alpha" is the alpha value of the indicator part of the ring.
        fg_alpha=0.2,
        -- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
        x=165, y=170,
        -- "radius" is the radius of the ring.
        radius=50,
        -- "thickness" is the thickness of the ring, centred around the radius.
        thickness=5,
        -- "start_angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
        start_angle=0,
        -- "end_angle" is the ending angle of the ring, in degrees, clockwise from top. Value can be either positive or negative, but must be larger (e.g. more clockwise) than start_angle.
        end_angle=360
    },
    

    {
        name='time',
        arg='%M.%S',
        max=60,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.4,
        x=165, y=170,
        radius=56,
        thickness=5,
        start_angle=0,
        end_angle=360
    },

    {
        name='time',
        arg='%S',
        max=60,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.6,
        x=165, y=170,
        radius=62,
        thickness=5,
        start_angle=0,
        end_angle=360
    },
]]
    {
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=0xFFFFFF,
        bg_alpha=0.1,
        fg_colour=0x1300FF,
        fg_alpha=0.8,
        x=165, y=600,
        radius=65,
        thickness=20,
        start_angle=125,
        end_angle=235
    },

    {
        name='battery_percent',
        arg='BAT0',
        max=100,
        bg_colour=0xFF0000,
        bg_alpha=0.2,
        fg_colour=0x00FF0F,
        fg_alpha=0.6,
        x=165, y=600,
        radius=80,
        thickness=11,
        start_angle=-90,
        end_angle=90
    },
    
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.8,
        x=165, y=600,
        radius=70,
        thickness=10,
        start_angle=245,
        end_angle=355
    },

    {
        name='swap',
        arg='/dev/sda2',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.8,
        x=165, y=600,
        radius=55,
        thickness=10,
        start_angle=245,
        end_angle=355
    },

    {
        name='fs_used_perc',
        arg='/',
        max=210,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xffffff,
        fg_alpha=0.3,
        x=165, y=600,
        radius=108.5,
        thickness=3,
        start_angle=-160,
        end_angle=160
    },
    
    {
        name='fs_used_perc',
        arg='/home',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xffffff,
        fg_alpha=0.3,
        x=165, y=600,
        radius=100,
        thickness=10,
        start_angle=-160,
        end_angle=160
    },

    {
        name='wireless_link_qual_perc',
        arg='wlan0',
        max=100,
        bg_colour=0xFFFFFF,
        bg_alpha=0.1,
        fg_colour=0xFF9E00,
        fg_alpha=0.8,
        x=165, y=600,
        radius=65,
        thickness=20,
        start_angle=5,
        end_angle=115
    },


--[[
    {
            name='downspeedf',
            arg='wlan0',
            max=2500,
            bg_colour=0x2F312E,
               bg_alpha=0.5,
            fg_colour=0xAAB364,
            fg_alpha=0.5,
            x=165, y=600,
        radius=20,
        thickness=10,
        start_angle=90,
        end_angle=270
        },
        {
            name='upspeedf',
            arg='wlan0',
            max=1500,
            bg_colour=0x2F312E,
            bg_alpha=0.5,
            fg_colour=0xAAB364,
            fg_alpha=0.5,
            x=165, y=600,
        radius=10,
        thickness=10,
        start_angle=-90,
        end_angle=90
        },

    {
        name='volume',
        arg='card0',
        max=100,
        bg_colour=0xFF9E00,
        bg_alpha=0.3,
        fg_colour=0xFF9E00,
        fg_alpha=0.7,
        x=165, y=600,
        radius=85,
        thickness=20,
        start_angle=5,
        end_angle=115
    },
]]

}
 
require 'cairo'
 
function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
 
function draw_ring(cr,t,pt)
    local w,h=conky_window.width,conky_window.height
 
    local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
 
    local angle_0=sa*(2*math.pi/360)-math.pi/2
    local angle_f=ea*(2*math.pi/360)-math.pi/2
    local t_arc=t*(angle_f-angle_0)
 

    -- Draw line
    
    --cairo_move_to(cr, 10, 10) --x, y
    --cairo_line_to(cr, 20, 20)
    --cairo_arc_to(cr, 60,50 )
        

    -- Draw background ring
 
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
 
    -- Draw indicator ring
 
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)
        

    -- Draw Text
    cairo_select_font_face (cr, "Sans", CAIRO_FONT_SLANT_NORMAL,
                               CAIRO_FONT_WEIGHT_BOLD);
    cairo_set_font_size (cr, 50.0);

    cairo_move_to (cr, 10.0, 755.0);
    cairo_show_text (cr, "Hello");

end
 
function conky_ring_stats()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
 
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
 
        value=tonumber(str)
        if value == nil then value = 0 end
        pct=value/pt['max']
 
        draw_ring(cr,pct,pt)
    end
 
    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
 
    local cr=cairo_create(cs)    
 
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
 
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
    end
end


```

Any help hugely appreciated. Thanks!

---

### Post by wlourf on 2010-06-04
you should write theses two lines 
```
cairo_move_to (cr, 10.0, 755.0);
cairo_show_text (cr, "Hello");
``` at the end of the conky_ring_stat function, not in the draw_ring function because this one is called multiple times.
hth !

---

### Post by bra|10n on 2010-06-04
> **Scooter_X said:**
> Hey, wondering if someone could help me with this strange problem. When I try to draw a line or text in my lua script, I get what you see in the screenshot. Lines dragging from my rings to my text/line. I just don't know why. I'm no programmer, so it's likely something simple but I wanted someone else to take a peek at my script:...
Any help hugely appreciated. Thanks!

I take it the "Hello" part is what you are referring to?
Try to leave the script intact and add 'extras' to the conkyrc that's calling that script. You no doubt will have to use ${offset} and ${voffset} and ${goto} for positioning.
Good luck!

---

### Post by dk75 on 2010-06-05
it's exactly as **wolfur@** said for drawing "Hello" by every ring procedure, so if you draw 4 rings then "**Hello**" text is drawn 4 time too.

But, moving text procedures will ease your CPU and Memory resource only, not drawing problem.

**"Hello"** text procedure is last and after that it's coordinates are remembered. There is no surface destroing after that to clean it up, or "**cairo_storke(cr)**" which also resets coordinates so in next loop lines are drawn from last know coordinates to next drawing possition.

So it need to be put "**cairo_storke(cr)**" after last "**cairo_show_text (cr, "text")**"

---

### Post by Darth_Beard on 2010-08-23
I hope someone can help me with my question.
I've modified londonali's rings script to inclide only the two cpu cores.

```
--[[
This is my testing purpose file for doings priests (sic)
with lua, cairo and conky
]]




settings_table = {
     {
        
        name='CPU core 1',
        arg='cpu1',
        --this ring will monitor core 1 of the CPU
        max=100,
        --100 since the conky variable returns a %age
        bg_color=0x483d8b,
        --background color is dark slate blue
        bg_alpha=0.3,
        --bg_color and bg_alpha are values for the base ring
        fg_color=0xa52a2a,
        --this color is brown
        fg_alpha=0.5
        --similar fg_color and fg_alpha are for the indicator part of the ring
        x=165, y=170,
        --x and y are the positions of the ring relative to the top left corner of the conky window
        radius=50,
        --radius is self explanatory
        thickness=5,
        --thickness determines how thick the ring is (centered around the radius)
        start_angle=0,
        end_angle=360,        
        },
        
        {
        name='CPU core 2',
        arg='cpu2',
        --this ring will monitor core 2 of the CPU
        max=100,
        --100 since the conky variable returns a %age
        bg_color=0x4b0082,
        --background color is indigo
        bg_alpha=0.3,
        --bg_color and bg_alpha are values for the base ring
        fg_color=0x80000,
        --this color is maroon
        fg_alpha=0.5
        --similar fg_color and fg_alpha are for the indicator part of the ring
        x=165, y=170,
        --x and y are the positions of the ring relative to the top left corner of the conky window
        radius=50,
        --radius is self explanatory
        thickness=5,
        --thickness determines how thick the ring is (centered around the radius)
        start_angle=0,
        end_angle=360,
        },
      }
        
        
 require 'cairo' 
 
 function rgb_to_r_g_b(color,alpha)
      return ((color / 0x10000) % 0x100) / 255., ((color / 0x100) % 0x100) /255., (color % 0x100) / 255., alpha
 end
 
 function draw_ring (cr,t,pt)
      local w,h=conky_window.width,conky_window.height
      
      local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
      local bgc, bga, fgc, fga=pt['bg_color'], pr['bg_alpha'], pt['fg_color'], pt['fg_alpha']
      
      local angle_0=sa*(2*math.pi/360)-math.pi/2
      local angle_0=ea*(2*math.pi/360)-math.pi/2
      local t_arc-t*(angle_f-angle_0)
      
      --draw background ring
      
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
 
    -- Draw indicator ring
 
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
end


function conky_ring_stats()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
 
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
 
        value=tonumber(str)
        if value == nil then value = 0 end
        pct=value/pt['max']
 
        draw_ring(cr,pct,pt)
    end
 
    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
 
    local cr=cairo_create(cs)    
 
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
 
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
    end
end
```
The .conkyrc lines that call it are

```
# -- Lua Load -- #
lua_load ~/.conky/testing_variables.lua
lua_draw_hook_pre ring_stats
```When I run conky from command line, I get 

```
Conky: llua_do_call: function conky_ring_stats execution failed: attempt to call a nil value
```Any help/sugestions would be appreciated.


Regards,

Darth_Beard

---

### Post by dk75 on 2010-08-23
feew typhos, here is DIFF

```
--- testing_variables.lua	2010-08-23 18:39:29.594872222 +0200
+++ test08.lua	2010-08-23 18:49:49.744249702 +0200
@@ -8,7 +8,6 @@
 
 settings_table = {
      {
-        
         name='CPU core 1',
         arg='cpu1',
         --this ring will monitor core 1 of the CPU
@@ -20,7 +19,7 @@
         --bg_color and bg_alpha are values for the base ring
         fg_color=0xa52a2a,
         --this color is brown
-        fg_alpha=0.5
+        fg_alpha=0.5,
         --similar fg_color and fg_alpha are for the indicator part of the ring
         x=165, y=170,
         --x and y are the positions of the ring relative to the top left corner of the conky window
@@ -44,7 +43,7 @@
         --bg_color and bg_alpha are values for the base ring
         fg_color=0x80000,
         --this color is maroon
-        fg_alpha=0.5
+        fg_alpha=0.5,
         --similar fg_color and fg_alpha are for the indicator part of the ring
         x=165, y=170,
         --x and y are the positions of the ring relative to the top left corner of the conky window
@@ -65,14 +64,12 @@
  end
  
  function draw_ring (cr,t,pt)
-      local w,h=conky_window.width,conky_window.height
-      
       local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
-      local bgc, bga, fgc, fga=pt['bg_color'], pr['bg_alpha'], pt['fg_color'], pt['fg_alpha']
+      local bgc, bga, fgc, fga=pt['bg_color'], pt['bg_alpha'], pt['fg_color'], pt['fg_alpha']
       
       local angle_0=sa*(2*math.pi/360)-math.pi/2
-      local angle_0=ea*(2*math.pi/360)-math.pi/2
-      local t_arc-t*(angle_f-angle_0)
+      local angle_f=ea*(2*math.pi/360)-math.pi/2
+      local t_arc=t*(angle_f-angle_0)
       
       --draw background ring
       
```

---

### Post by Darth_Beard on 2010-08-24
Thank you for the reply.  :KS
I need to go through londonali's code and try to understand the functions used to draw the rings as I'm having problems with them.

Thanks again.

Darth_Beard

---

### Post by jo-shva on 2010-09-14
I cant seem figure out how to show additional devices. arg=conky_parse("${fs_used_perc /media/}"), 
works for only one media device. i would like to have it read any additional devices i have plugged.
Is this posible?
 
{
	name="",
	arg=conky_parse("${fs_used_perc /media/}"),
	max=100,
	xc=130,
	yc=516,
	thickness=70,
	radius=70,
	start_angle=144,
	end_angle=216,
	sectors=100,
	gap_sectors=-1,
	bg_colour2={{0,0X111111,1},{0.75,0x111111,1}, {1,0x888888,1}},
	bg_colour1={{0,0X999999,1},{0.75,0x888888,1}, {1,0x111111,1}},
	fg_colour2={{0,0XFF4500,1},{0.75,0xFF4500,1}, {1,0xFFFFFF,1}},
	fg_colour1={{0,0XFFFFFF,1},{0.75,0xFFFFFF,1}, {1,0xFF4500,1}},
	},
	{
	name="fs_used_perc",
	arg="/media/''",
	max=100,
	xc=130,
	yc=516,
	thickness=70,
	radius=70,
	start_angle=216,
	end_angle=288,
	sectors=100,
	gap_sectors=-1,
	bg_colour2={{0,0X111111,1},{0.75,0x111111,1}, {1,0x888888,1}},
	bg_colour1={{0,0X999999,1},{0.75,0x888888,1}, {1,0x111111,1}},
	fg_colour2={{0,0XFF4500,1},{0.75,0xFF4500,1}, {1,0xFFFFFF,1}},
	fg_colour1={{0,0XFFFFFF,1},{0.75,0xFFFFFF,1}, {1,0xFF4500,1}},
	},
}
im stuck:confused:

---

### Post by dk75 on 2010-09-14
use the **CODE** tag Luke, use the **CODE**

As for question - it can't be done with one Conky command but it is possible with feew lines of code in LUA or BASH or PYTHON or PERL.

---

### Post by jo-shva on 2010-09-15
thanks obi-wan.  I am doing my best to use the CODE.  the trouble is i haven't found the appropriate CODE to achieve said task...ie: hot-pluggable devices to show.  It would be of great help if you could show me/lead me to the right coding. Please!
Ill paste my Lua here and screenshot of what i have so far.


```
--[[ RINGS with SECTORS widget
	v1.0 by wlourf (08.08.2010)
	this widget draws a ring with differents effects 
	http://u-scripts.blogspot.com/2010/08/rings-sectors-widgets.html
	
To call the script in a conky, use, before TEXT
	lua_load /path/to/the/script/rings.lua
	lua_draw_hook_pre main_rings
and add one line (blank or not) after TEXT


Parameters are :
3 parameters are mandatory
name		- the name of the conky variable to display,
			  for example for {$cpu cpu0}, just write name="cpu"
arg			- the argument of the above variable,
			  for example for {$cpu cpu0}, just write arg="cpu0"
		  	  arg can be a numerical value if name=""
max			- the maximum value the above variable can reach,
			  for example for {$cpu cpu0}, just write max=100
	
Optional parameters:
xc,yc		- coordinates of the center of the ring,
			  default = middle of the conky window
radius		- external radius of the ring, in pixels,
			  default = quarter of the width of the conky window
thickness	- thickness of the ring, in pixels, default = 10 pixels
start_angle	- starting angle of the ring, in degrees, value can be negative,
			  default = 0 degree
end_angle	- ending angle of the ring, in degrees,
			  value must be greater than start_angle, default = 360 degrees
sectors		- number of sectors in the ring, default = 10
gap_sectors - gap between two sectors, in pixels, default = 1 pixel
cap			- the way to close a sector, available values are
				"p" for parallel , default value 
				"r" for radial (follow the radius)
inverse_arc	- if set to true, arc will be anticlockwise, default=false
border_size	- size of the border, in pixels, default = 0 pixel i.e. no border
fill_sector	- if set to true, each sector will be completely filled,
			  default=false, this parameter is inoperate if sectors=1
background	- if set to false, background will not be drawn, default=true
foreground	- if set to false, foreground will not be drawn, default=true

Colours tables below are defined into braces :
{position in the gradient (0 to 1), colour in hexadecimal, alpha (0 to 1)}
example for a single colour table : 
{{0,0xFFAA00,1}} position parameter doesn't matter
example for a two-colours table : 
{{0,0xFFAA00,1},{1,0x00AA00,1}} or {{0.5,0xFFAA00,1},{1,0x00AA00,1}}
example for a three-colours table : 
{{0,0xFFAA00,1},{0.5,0xFF0000,1},{1,0x00AA00,1}}

bg_colour1	- colour table for background,
			  default = {{0,0x00ffff,0.1},{0.5,0x00FFFF,0.5},{1,0x00FFFF,0.1}}
fg_colour1	- colour table for foreground,
			  default = {{0,0x00FF00,0.1},{0.5,0x00FF00,1},{1,0x00FF00,0.1}}
bd_colour1	- colour table for border,
			  default = {{0,0xFFFF00,0.5},{0.5,0xFFFF00,1},{1,0xFFFF00,0.5}}			  

Seconds tables for radials gradients :
bg_colour2	- second colour table for background, default = no second colour
fg_colour2	- second colour table for foreground, default = no second colour
bd_colour2	- second colour table for border, default = no second colour

v1.0 (08 Aug. 2010) original release

]]


require 'cairo'
function conky_main_rings()
-- START PARAMETERS HERE
rings_settings={
--line1 CPU
	--under shadow 
	--[[{
	name="",
	arg="",
	max=100,
	xc=130,
	yc=80,
	radius=40,
	thickness=10,
	start_angle=-120,
	end_angle=120,
	sectors=40,
	bg_colour1={{0,0x000000,0.3},{0.5,0x000000,0.5}, {1,0x000000,0.3}},
	fg_colour1={{0,0X000000,0.2},{0.5,0x000000,0.5}, {1,0x000000,0.2}},
	fg_colour2={{0,0XFF0000,0},{0.5,0xFF0000,0}, {1,0xFF0000,0}},
	bd_colour1={{0,0X00FF00,0},{0.5,0x00FF00,0}, {1,0x00FF00,0}},
	},
	
	{
	name="",
	arg="",
	max=100,
	xc=130,
	yc=80,
	radius=50,
	thickness=10,
	start_angle=-120,
	end_angle=120,
	sectors=40,
	bg_colour1={{0,0x000000,0.3},{0.5,0x000000,0.5}, {1,0x000000,0.3}},
	fg_colour1={{0,0X000000,0.2},{0.5,0x000000,0.5}, {1,0x000000,0.2}},
	fg_colour2={{0,0XFF0000,0},{0.5,0xFF0000,0}, {1,0xFF0000,0}},
	bd_colour1={{0,0X00FF00,0},{0.5,0x00FF00,0}, {1,0x00FF00,0}},
	},]]
	{
	name="",
	arg="",
	max=30,
	xc=130,
	yc=80,
	thickness=49,
	radius=49,
	start_angle=0,
	end_angle=360,
	sectors=1,
	gap_sectors=-1,
	bg_colour2={{0,0X000000,0.5},{0.75,0x000000,0.5}, {1,0x000000,0.5}},
	bg_colour1={{0,0X000000,0.5},{0.75,0x000000,0.5}, {1,0x000000,0.5}},
	fg_colour2={{0,0XFF4500,0},{0.75,0xFF4500,0}, {1,0xFFFFFF,0}},
	fg_colour1={{0,0XFFFFFF,0},{0.75,0xFFFFFF,0}, {1,0xFF4500,0}},
	},
	--end cpu shadows
	
	--rings temp sensor behind shadows
	--[[{
	--ring 4-1 : temperature cpu1
	name="",
	arg="",
	max=60,
	xc=130,
	yc=80,
	radius=74,
	thickness=10,
	gap_sectors=7,
	sectors=40,
	start_angle=120,
	end_angle=420,
	bg_colour1={{0,0x000000,0.2},{0.5,0x000000,0.5}, {1,0x00000,0.2}},
	fg_colour1={{0,0X000000,0.2},{0.5,0x000000,0.2}, {1,0x00000,0.2}},
	fg_colour2={{0,0XFF0000,0},{0.5,0xFF0000,0}, {1,0xFF0000,0}},
	bd_colour1={{0,0X00FF00,0},{0.5,0x00FF00,0}, {1,0x00FF00,0}},
	},	
	
		
	{
	--ring 4-2 : temp cup2
	name="",
	arg="",
	max=64,
	xc=130,
	yc=80,
	radius=64,
	thickness=10,
	gap_sectors=7,
	sectors=40,
	start_angle=120,
	end_angle=420,
	bg_colour1={{0,0x000000,0.2},{0.5,0x000000,0.5}, {1,0x000000,0.2}},
	fg_colour1={{0,0X000000,0.2},{0.5,0x000000,0.2}, {1,0x000000,0.2}},
	fg_colour2={{0,0XFF0000,0},{0.5,0xFF0000,0}, {1,0xFF0000,0}},
	bd_colour1={{0,0X00FF00,0},{0.5,0x00FF00,0}, {1,0x00FF00,0}},
	},]]
	{
	name="",
	arg="",
	max=30,
	xc=130,
	yc=80,
	thickness=24,
	radius=73,
	start_angle=59,
	end_angle=-239,
	sectors=1,
	gap_sectors=-1,
	bg_colour2={{0,0X000000,0.5},{0.85,0x000000,0.2}, {1,0x000000,0}},
	bg_colour1={{0,0X000000,0.5},{0.85,0x000000,0.2}, {1,0x000000,0}},
	fg_colour2={{0,0XFF4500,0},{0.75,0xFF4500,0}, {1,0xFFFFFF,0}},
	fg_colour1={{0,0XFFFFFF,0},{0.75,0xFFFFFF,0}, {1,0xFF4500,0}},
	},
	--end shadows temperature
	
	{
	--ring 4-2 : temp cup2
	name="exec",
	arg="sensors -f | grep 'temp2' | cut -c15-16",
	max=60,
	xc=130,
	yc=80,
	radius=69,
	thickness=12,
	start_angle=121,
	end_angle=419,
	bg_colour1={{0,0xB5B5E1,0},{0.5,0xB5B5E1,1}, {1,0xB5B5E1,0}},
	bg_colour2={{0,0x1B1A25,0},{0.5,0x5D5D78,1}, {1,0x5D5D78,0}},
	fg_colour1={{0,0XffFF00,0},{0.5,0xffFF00,1}, {1,0xffFF00,0}},
	fg_colour2={{0,0XFF0000,0},{0.5,0xFF0000,1}, {1,0xFF0000,0}},
	bd_colour1={{0,0X00FF00,1},{0.5,0x00FF00,1}, {1,0x00FF00,1}},
	},
	
	{
	--ring 4-1 : temperature cpu1
	name="exec",
	arg="sensors -f | grep 'temp1' | cut -c15-16",
	max=60,
	xc=130,
	yc=80,
	radius=74,
	thickness=10,
	sectors=60,
	gap_sectors=4,
	fill_sectors=true,
	start_angle=120,
	end_angle=420,
	bg_colour1={{0,0xB5B5E1,0},{0.5,0xB5B5E1,1}, {1,0xB5B5E1,0}},
	bg_colour2={{0,0x1B1A25,0},{0.5,0x5D5D78,1}, {1,0x5D5D78,0}},
	fg_colour1={{0,0XffFF00,0},{0.5,0xffFF00,1}, {1,0xffFF00,0}},
	fg_colour2={{0,0XFF0000,0},{0.5,0xFF0000,1}, {1,0xFF0000,0}},
	bd_colour1={{0,0X00FF00,1},{0.5,0x00FF00,1}, {1,0x00FF00,1}},
	},	
	
	
	--top CPU
	{
	name="cpu",
	arg="cpu0",
	max=100,
	xc=130,
	yc=80,
	radius=47,
	thickness=10,
	start_angle=-126,
	end_angle=128,
	sectors=40,
	bg_colour1={{0,0x737393,0},{0.5,0xB5B5E1,1}, {1,0x737393,0}},
	fg_colour1={{0,0X0000ff,0},{0.5,0x0000ff,1}, {1,0x0000ff,0}},
	fg_colour2={{0,0X000033,0},{0.5,0x000033,1}, {1,0x000033,0}},
	bd_colour1={{0,0X00FF00,1},{0.5,0x00FF00,1}, {1,0x00FF00,1}},
	},
	
	
	{
	name="cpu",
	arg="cpu1",
	max=100,
	xc=130,
	yc=80,
	radius=55,
	thickness=10,
	start_angle=-132,
	end_angle=134,
	sectors=40,
	bg_colour1={{0,0x9697BC,0},{0.5,0xB5B5E1,1}, {1,0x9697BC,0}},
	fg_colour1={{0,0X0033ff,0},{0.5,0x0033ff,1}, {1,0x0033ff,0}},
	fg_colour2={{0,0X000033,0},{0.5,0x000033,1}, {1,0x000033,0}},
	bd_colour1={{0,0X00FF00,1},{0.5,0x00FF00,1}, {1,0x00FF00,1}},
	},
	
	--mem piefill
	{
	name="",
	arg="",
	max=30,
	xc=130,
	yc=235,
	thickness=60,
	radius=60,
	start_angle=0,
	end_angle=360,
	sectors=1,
	gap_sectors=-1,
	bg_colour2={{0,0X000000,0.5},{0.85,0x000000,0.2}, {1,0x000000,0}},
	bg_colour1={{0,0X000000,0.5},{0.85,0x000000,0.2}, {1,0x000000,0}},
	fg_colour2={{0,0XFF4500,0},{0.75,0xFF4500,0}, {1,0xFFFFFF,0}},
	fg_colour1={{0,0XFFFFFF,0},{0.75,0xFFFFFF,0}, {1,0xFF4500,0}},
	},
	
	--2 rings to draw a full circle MEM
	{
	name="",
	arg="",
	max=30,
	xc=130,
	yc=235,
	thickness=20,
	radius=60,
	start_angle=0,
	end_angle=180,
	bg_colour1={{0,0X1B1A25,0.6},{0.5,0x1B1A25,1}, {1,0x5D5D78,0.6}},
	bg_colour2={{0,0XB5B5E1,0.5},{0.5,0x5D5D78,1}, {1,0x1B1A25,0.5}},
	fg_colour1={{0,0XFF4500,1},{0.5,0xFF4500,1}, {1,0xFFFFFF,1}},
	fg_colour2={{0,0XFFFFFF,1},{0.5,0xFFFFFF,1}, {1,0xFF4500,1}},
	},
	{
	name="",
	arg="",
	max=30,
	xc=130,
	yc=235,
	thickness=20,
	radius=60,
	start_angle=180,
	end_angle=360,
	bg_colour2={{0,0X1B1A25,0.6},{0.5,0x1B1A25,1}, {1,0x5D5D78,0.6}},
	bg_colour1={{0,0XB5B5E1,0.5},{0.5,0x5D5D78,1}, {1,0x1B1A25,0.5}},
	fg_colour2={{0,0XFF4500,1},{0.5,0xFF4500,1}, {1,0xFFFFFF,1}},
	fg_colour1={{0,0XFFFFFF,1},{0.5,0xFFFFFF,1}, {1,0xFF4500,1}},
	},	
	
	--two rings to mem meter inside circles
		{
	name="memperc",
	arg="",
	max=50,
	xc=130,
	yc=235,
	thickness=20,
	radius=60,
	start_angle=0,
	end_angle=180,
	bg_colour1={{0,0X111111,0},{0.5,0x111111,0}, {1,0x888888,0}},
	bg_colour2={{0,0X999999,0},{0.5,0x888888,0}, {1,0x111111,0}},
	fg_colour1={{0,0X272763,0.7},{0.5,0x272763,1}, {1,0xB4B4E6,0.7}},
	fg_colour2={{0,0XB4B4E6,0.6},{0.5,0xB4B4E6,1}, {1,0x272763,0.6}},
	},
	{
	name="",
	arg=conky_parse("${memperc}")-50,
	max=50,
	xc=130,
	yc=235,
	thickness=20,
	radius=60,
	start_angle=180,
	end_angle=360,
	bg_colour2={{0,0X111111,0},{0.5,0x111111,0}, {1,0x888888,0}},
	bg_colour1={{0,0X999999,0},{0.5,0x888888,0}, {1,0x111111,0}},
	fg_colour2={{0,0X272763,0.7},{0.5,0x272763,1}, {1,0xB4B4E6,0.7}},
	fg_colour1={{0,0XB4B4E6,0.6},{0.5,0xB4B4E6,1}, {1,0x272763,0.6}},
	},
	
	--swap
	{
	name="",
	arg="",
	max=30,
	xc=130,
	yc=235,
	thickness=8,
	radius=74,
	start_angle=180,
	end_angle=360,
	bg_colour2={{0,0X1B1A25,0.6},{0.5,0x1B1A25,1}, {1,0x39394E,0.6}},
	bg_colour1={{0,0X68686D,0.5},{0.5,0x39394E,1}, {1,0x1B1A25,0.5}},
	fg_colour2={{0,0XFF4500,0},{0.5,0xFF4500,0}, {1,0xFFFFFF,0}},
	fg_colour1={{0,0XFFFFFF,0},{0.5,0xFFFFFF,0}, {1,0xFF4500,0}},
	},	
	
	{
	name="swap",
	arg="",
	max=100,
	xc=130,
	yc=235,
	thickness=8,
	radius=74,
	start_angle=0,
	end_angle=-180,
	bg_colour2={{0,0X1B1A25,0},{0.5,0x1B1A25,0}, {1,0x39394E,0}},
	bg_colour1={{0,0X68686D,0},{0.5,0x39394E,0}, {1,0x1B1A25,0}},
	fg_colour2={{0,0X464A1D,0.7},{0.5,0x464A1D,1}, {1,0x848442,0.7}},
	fg_colour1={{0,0XD2D2A7,0.6},{0.5,0x848442,1}, {1,0x464A1D,0.6}},
	},
	
	--[[{
	--right half ring 5 : download speed
	name="downspeedf",
	arg="wlan0",
	max=400,
	xc=130,
	yc=355,
	radius=40,
	thickness=10,
	end_angle=180,
	sectors=30,
	fill_sector=true,
	bg_colour1={{0,0X1B1A25,0.7},{0.5,0x1B1A25,1}, {1,0x5D5D78,0.7}},
	bg_colour2={{0,0XB5B5E1,0.6},{0.5,0x5D5D78,1}, {1,0x1B1A25,0.6}},
	fg_colour1={{0,0X215F21,0.7},{0.5,0x215F21,1}, {1,0x00ff00,0.7}},
	fg_colour2={{0,0X8BDE8B,0.7},{0.5,0x00ff00,1}, {1,0x215F21,0.7}},
	bd_colour1={{0,0X00FF00,1},{0.5,0x00FF00,1}, {1,0x00FF00,1}},
	},
	{
	--left half ring 5 : upload speed
	name="upspeedf",
	arg="wlan0",
	max=100,
	xc=130,
	yc=355,
	radius=40,
	thickness=10,
	start_angle=360,
	end_angle=180,
	inverse_arc=true,
	sectors=30,
	fill_sector=true,
	bg_colour2={{0,0X1B1A25,0.7},{0.5,0x1B1A25,1}, {1,0x5D5D78,0.7}},
	bg_colour1={{0,0XB5B5E1,0.6},{0.5,0x5D5D78,1}, {1,0x1B1A25,0.6}},
	fg_colour1={{0,0x8B5A1D,1},{0.5,0x8B5A1D,1}, {1,0xFF9809,1}},
	fg_colour2={{0,0XEBD7A3,1},{0.5,0xFF9809,1}, {1,0x8B5A1D,1}},
	bd_colour1={{0,0X00FF00,1},{0.5,0x00FF00,1}, {1,0x00FF00,1}},
	},]]
	--Network bottom piefill
	{
	name="",
	arg="",
	max=30,
	xc=122,
	yc=380,
	thickness=56,
	radius=56,
	start_angle=88,
	end_angle=270,
	sectors=1,
	gap_sectors=-1,
	bg_colour2={{0,0X000000,0.5},{0.90,0x000000,0.2}, {1,0x000000,0}},
	bg_colour1={{0,0X000000,0.5},{0.90,0x000000,0.2}, {1,0x000000,0}},
	fg_colour2={{0,0XFF4500,0},{0.75,0xFF4500,0}, {1,0xFFFFFF,0}},
	fg_colour1={{0,0XFFFFFF,0},{0.75,0xFFFFFF,0}, {1,0xFF4500,0}},
	},
	--Network bottom pie Sliver
	{
	name="",
	arg="",
	max=30,
	xc=122,
	yc=382,
	thickness=8,
	radius=57,
	start_angle=130,
	end_angle=230,
	sectors=1,
	gap_sectors=-1,
	bg_colour2={{0.4,0x000000,0.1}, {1,0x000000,0}},
	bg_colour1={{0.4,0x000000,0.1}, {1,0x000000,0}},
	fg_colour2={{0,0XFF4500,0},{0.75,0xFF4500,0}, {1,0xFFFFFF,0}},
	fg_colour1={{0,0XFFFFFF,0},{0.75,0xFFFFFF,0}, {1,0xFF4500,0}},
	},
	--Network top piefill
	{
	name="",
	arg="",
	max=30,
	xc=134,
	yc=380,
	thickness=68,
	radius=68,
	start_angle=87,
	end_angle=-90,
	sectors=1,
	gap_sectors=-1,
	bg_colour2={{0,0X000000,0.5},{0.85,0x000000,0.2}, {1,0x000000,0}},
	bg_colour1={{0,0X000000,0.5},{0.85,0x000000,0.2}, {1,0x000000,0}},
	fg_colour2={{0,0XFF4500,0},{0.75,0xFF4500,0}, {1,0xFFFFFF,0}},
	fg_colour1={{0,0XFFFFFF,0},{0.75,0xFFFFFF,0}, {1,0xFF4500,0}},
	},
	
	--test wlan0
	--[[{
	name="",
	arg="",
	max=60,
	xc=130,
	yc=380,
	thickness=30,
	radius=74,
	sectors=50,
	gap_sectors=3,
	start_angle=180,
	end_angle=450,
	fill_sectors=true,
	fg_colour1={{0.49,0x000000,1},{0.5,0x000000,1},{0.51,0x000000,1}},
	fg_colour2={{0,0x000000,1},{0.5,0x000000,1},{1,0x000000,1}},
	bg_colour1={{0.49,0x000000,0},{0.5,0x000000,1},{0.51,0x000000,0}},
	bg_colour2={{0,0x000000,0},{0.5,0x000000,1},{1,0x000000,0}},
	},
	
	{
	name="",
	arg="",
	max=60,
	xc=130,
	yc=380,
	thickness=30,
	radius=64,
	gap_sectors=3,
	start_angle=-90,
	end_angle=180,
	sectors=40,
	fg_colour1={{0.49,0x000000,1},{0.5,0x000000,1},{0.51,0x000000,1}},
	fg_colour2={{0,0x000000,1},{0.5,0x000000,1},{1,0x000000,1}},
	bg_colour1={{0.49,0x000000,0},{0.5,0x000000,1},{0.51,0x000000,0}},
	bg_colour2={{0,0x000000,0},{0.5,0x000000,1},{1,0x000000,0}},
	},]]
			
	-- wlan0 up
	{
	name="upspeedf",
	arg="wlan0",
	max=55,
	xc=130,
	yc=380,
	thickness=30,
	radius=74,
	sectors=50,
	gap_sectors=3,
	fill_sectors=true,
	start_angle=186,
	end_angle=450,
	fg_colour1={{0.49,0xFFFF00,0},{0.5,0xFFFF00,1},{0.51,0x00FF00,0}},
	fg_colour2={{0,0xFF0000,0},{0.5,0xffff00,1},{1,0xFF0000,0}},
	bg_colour1={{0.49,0xB5B5E1,0},{0.5,0xB5B5E1,1},{0.51,0x1B1A25,0}},
	bg_colour2={{0,0x1B1A25,0},{0.5,0x5D5D78,1},{1,0x5D5D78,0}},
	},
	-- wlan0 down
	{
	name="downspeedf",
	arg="wlan0",
	max=300,
	xc=123,
	yc=380,
	thickness=30,
	radius=60,
	gap_sectors=3,
	start_angle=-90,
	end_angle=180,
	sectors=40,
	fill_sectors=true,
	fg_colour1={{0.49,0xFFFF00,0},{0.5,0x00FF00,1},{0.51,0x00FF00,0}},
	fg_colour2={{0,0xFF0000,0},{0.5,0x00ff00,1},{1,0xFF0000,0}},
	bg_colour1={{0.49,0xffFFFF,0},{0.5,0x5D5D78,1},{0.51,0xffFFFF,0}},
	bg_colour2={{0,0x000000,0},{0.5,0xB5B5E1,1},{1,0x000000,0}},
	},
	
	--HD 2 rings to draw a full circle				
	
	
	--[[{
	name="fs_used_perc",
	arg="/windows",
	max=100,
	xc=130,
	yc=516,
	thickness=20,
	radius=60,
	start_angle=144,
	end_angle=216,
	sectors=100,
	gap_sectors=-1,
	bg_colour2={{0,0X111111,1},{0.75,0x111111,1}, {1,0x888888,1}},
	bg_colour1={{0,0X999999,1},{0.75,0x888888,1}, {1,0x111111,1}},
	fg_colour2={{0,0XFF4500,1},{0.75,0xFF4500,1}, {1,0xFFFFFF,1}},
	fg_colour1={{0,0XFFFFFF,1},{0.75,0xFFFFFF,1}, {1,0xFF4500,1}},
	},]]
	--[[{
	name="fs_used_perc",
	arg="/media/",
	max=100,
	xc=130,
	yc=516,
	thickness=30,
	radius=74,
	start_angle=216,
	end_angle=288,
	sectors=100,
	gap_sectors=-1,
	bg_colour2={{0,0X111111,1},{0.75,0x111111,1}, {1,0x888888,1}},
	bg_colour1={{0,0X999999,1},{0.75,0x888888,1}, {1,0x111111,1}},
	fg_colour2={{0,0XFF4500,1},{0.75,0xFF4500,1}, {1,0xFFFFFF,1}},
	fg_colour1={{0,0XFFFFFF,1},{0.75,0xFFFFFF,1}, {1,0xFF4500,1}},
	},
	{
	name="fs_used_perc",
	arg="/media/",
	max=100,
	xc=130,
	yc=516,
	thickness=30,
	radius=74,
	start_angle=288,
	end_angle=360,
	sectors=100,
	gap_sectors=-1,
	bg_colour2={{0,0X111111,1},{0.75,0x111111,1}, {1,0x888888,1}},
	bg_colour1={{0,0X999999,1},{0.75,0x888888,1}, {1,0x111111,1}},
	fg_colour2={{0,0XFF4500,1},{0.75,0xFF4500,1}, {1,0xFFFFFF,1}},
	fg_colour1={{0,0XFFFFFF,1},{0.75,0xFFFFFF,1}, {1,0xFF4500,1}},
	},]]
	--HD Clock piefill
	{
	name="",
	arg="",
	max=30,
	xc=130,
	yc=526,
	thickness=60,
	radius=60,
	start_angle=0,
	end_angle=360,
	sectors=1,
	gap_sectors=-1,
	bg_colour2={{0,0X000000,0.5},{0.85,0x000000,0.2}, {1,0x000000,0}},
	bg_colour1={{0,0X000000,0.5},{0.85,0x000000,0.2}, {1,0x000000,0}},
	fg_colour2={{0,0XFF4500,0},{0.75,0xFF4500,0}, {1,0xFFFFFF,0}},
	fg_colour1={{0,0XFFFFFF,0},{0.75,0xFFFFFF,0}, {1,0xFF4500,0}},
	},
	--end piefill
	{
	name="fs_used_perc",
	arg="/",
	max=100,
	xc=130,
	yc=526,
	thickness=20,
	radius=60,
	start_angle=5,
	end_angle=96,
	sectors=1,
	gap_sectors=-1,
	bg_colour1={{0,0X5D5D78,0.5},{0.5,0x5D5D78,0.7}, {1,0x5D5D78,0.5}},
	bg_colour2={{0,0X5D5D78,0.5},{0.5,0x5D5D78,0.7}, {1,0x5D5D78,0.5}},
	fg_colour1={{0,0X7f7f3c,0.5},{0.75,0x7f7f3c,0.7}, {1,0x7f7f3c,0.5}},
	fg_colour2={{0,0X7f7f3c,0.5},{0.75,0x7f7f3c,0.7}, {1,0x7f7f3c,0.5}},
	},
	{
	name="fs_used_perc",
	arg="/home",
	max=100,
	xc=130,
	yc=526,
	thickness=20,
	radius=60,
	start_angle=106,
	end_angle=355,
	sectors=1,
	gap_sectors=-1,
	bg_colour1={{0,0X5D5D78,0.5},{0.5,0x5D5D78,0.7}, {1,0x5D5D78,0.5}},
	bg_colour2={{0,0X5D5D78,0.5},{0.5,0x5D5D78,0.7}, {1,0x5D5D78,0.5}},
	fg_colour1={{0,0X7f7f3c,0.5},{0.75,0x7f7f3c,0.7}, {1,0x7f7f3c,0.5}},
	fg_colour2={{0,0X7f7f3c,0.5},{0.75,0x7f7f3c,0.7}, {1,0x7f7f3c,0.5}},
	},
	
	--inner clock ring
	{
	name="time",
	arg="%S",
	max=30,
	xc=130,
	yc=526,
	thickness=8,
	radius=47,
	start_angle=0,
	end_angle=180,
	sectors=6,
	gap_sectors=1,
	bg_colour1={{0,0X1B1A25,1},{0.5,0x1B1A25,1}, {1,0x5D5D78,1}},
	bg_colour2={{0,0XB5B5E1,1},{0.5,0x5D5D78,1}, {1,0x1B1A25,1}},
	fg_colour1={{0,0X272763,0.7},{0.5,0x272763,1}, {1,0xB4B4E6,0.7}},
	fg_colour2={{0,0XB4B4E6,0.6},{0.5,0xB4B4E6,1}, {1,0x272763,0.6}},
	},
	{
	name="",
	arg=conky_parse("${time  %S}")-30,
	max=30,
	xc=130,
	yc=526,
	thickness=8,
	radius=47,
	start_angle=180,
	end_angle=360,
	sectors=6,
	gap_sectors=1,
	bg_colour2={{0,0X1B1A25,1},{0.5,0x1B1A25,1}, {1,0x5D5D78,1}},
	bg_colour1={{0,0XB5B5E1,1},{0.5,0x5D5D78,1}, {1,0x1B1A25,1}},
	fg_colour2={{0,0X272763,0.7},{0.5,0x272763,1}, {1,0xB4B4E6,0.7}},
	fg_colour1={{0,0XB4B4E6,0.6},{0.5,0xB4B4E6,1}, {1,0x272763,0.6}},
	},
	--center alpha rings
	{
	name="",
	arg="",
	max=30,
	xc=130,
	yc=526,
	thickness=3,
	radius=33,
	start_angle=0,
	end_angle=360,
	sectors=1,
	gap_sectors=-1,
	bg_colour1={{0,0XB5B5E1,0.1},{0.5,0xB5B5E1,0.1}, {1,0xB5B5E1,0.1}},
	bg_colour2={{0,0XB5B5E1,0.1},{0.5,0xB5B5E1,0.1}, {1,0xB5B5E1,0.1}},
	fg_colour1={{0,0X272763,0},{0.5,0x272763,0}, {1,0xB4B4E6,0}},
	fg_colour2={{0,0XB4B4E6,0},{0.5,0xB4B4E6,0}, {1,0x272763,0}},
	},
	{
	name="",
	arg="",
	max=30,
	xc=130,
	yc=526,
	thickness=3,
	radius=23,
	start_angle=0,
	end_angle=360,
	sectors=1,
	gap_sectors=-1,
	bg_colour1={{0,0XB5B5E1,0.1},{0.5,0xB5B5E1,0.1}, {1,0xB5B5E1,0.1}},
	bg_colour2={{0,0XB5B5E1,0.1},{0.5,0xB5B5E1,0.1}, {1,0xB5B5E1,0.1}},
	fg_colour1={{0,0X272763,0},{0.5,0x272763,0}, {1,0xB4B4E6,0}},
	fg_colour2={{0,0XB4B4E6,0},{0.5,0xB4B4E6,0}, {1,0x272763,0}},
	},
	{
	name="",
	arg="",
	max=30,
	xc=130,
	yc=526,
	thickness=3,
	radius=13,
	start_angle=0,
	end_angle=360,
	sectors=1,
	gap_sectors=-1,
	bg_colour1={{0,0XB5B5E1,0.1},{0.5,0xB5B5E1,0.1}, {1,0xB5B5E1,0.1}},
	bg_colour2={{0,0XB5B5E1,0.1},{0.5,0xB5B5E1,0.1}, {1,0xB5B5E1,0.1}},
	fg_colour1={{0,0X272763,0},{0.5,0x272763,0}, {1,0xB4B4E6,0}},
	fg_colour2={{0,0XB4B4E6,0},{0.5,0xB4B4E6,0}, {1,0x272763,0}},
	},
	--[[{
	name="time",
	arg="%I",
	max=60,
	xc=130,
	yc=526,
	size=74,
	alpha=1,
	colour={0x000000},
	},]]
	
	--[[
	name="fs_used_perc",
	arg="/var",
	max=100,
	xc=130,
	yc=516,
	thickness=30,
	radius=68,
	start_angle=264,
	end_angle=313,
	sectors=100,
	gap_sectors=-1,
	bg_colour1={{0,0X111111,1},{0.75,0x111111,1}, {1,0x888888,1}},
	bg_colour2={{0,0X999999,1},{0.75,0x888888,1}, {1,0x111111,1}},
	fg_colour1={{0,0XFF4500,1},{0.75,0xFF4500,1}, {1,0xFFFFFF,1}},
	fg_colour2={{0,0XFFFFFF,1},{0.75,0xFFFFFF,1}, {1,0xFF4500,1}},
	},
	{
	name="fs_used_perc",
	arg="/tmp",
	max=100,
	xc=130,
	yc=516,
	thickness=30,
	radius=68,
	start_angle=318,
	end_angle=355,
	sectors=100,
	gap_sectors=-1,
	bg_colour2={{0,0X111111,1},{0.75,0x111111,1}, {1,0x888888,1}},
	bg_colour1={{0,0X999999,1},{0.75,0x888888,1}, {1,0x111111,1}},
	fg_colour2={{0,0XFF4500,1},{0.75,0xFF4500,1}, {1,0xFFFFFF,1}},
	fg_colour1={{0,0XFFFFFF,1},{0.75,0xFFFFFF,1}, {1,0xFF4500,1}},
	},]]
}
--END OF PARAMETERS HERE

--main function

	if conky_window==nil then return end

	local cs=cairo_xlib_surface_create(conky_window.display,
		conky_window.drawable, 
		conky_window.visual, conky_window.width, conky_window.height)
	cr=cairo_create(cs)

	if tonumber(conky_parse('${updates}'))>3 then
		for i in pairs(rings_settings) do
			draw_ring(rings_settings[i])
		end
	end

	cairo_destroy(cr)

end




function draw_ring(t)

	local function rgba_to_r_g_b_a(tcolour)
		colour,alpha=tcolour[2],tcolour[3]
		return ((colour / 0x10000) % 0x100) / 255., 
			((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end
			
			
	local function calc_delta(tcol1,tcol2)
		--calculate deltas P R G B A to table_colour 1

		for x = 1, #tcol1 do
			tcol1[x].dA	= 0
			tcol1[x].dP = 0
	 		tcol1[x].dR = 0
			tcol1[x].dG = 0
			tcol1[x].dB = 0
			if tcol2~=nil and #tcol1 == #tcol2 then
				local r1,g1,b1,a1 = rgba_to_r_g_b_a(tcol1[x])
				local r2,g2,b2,a2 = rgba_to_r_g_b_a(tcol2[x])
				tcol1[x].dP = (tcol2[x][1]-tcol1[x][1])/t.sectors
		 		tcol1[x].dR = (r2-r1)/t.sectors
				tcol1[x].dG = (g2-g1)/t.sectors
				tcol1[x].dB = (b2-b1)/t.sectors
				tcol1[x].dA = (a2-a1)/t.sectors		
				
			end
		end
		
		return tcol1
	end

	--check values
	local function setup(t)
		if t.name==nil and t.arg==nil then 
			print ("No input values ... use parameters 'name'" +
				" with 'arg' or only parameter 'arg' ") 
			return
		end

		if t.max==nil then
			print ("No maximum value defined, use 'max'")
			print ("for name=" .. t.name)
			print ("with arg=" .. t.arg)
			return
		end
		if t.name==nil then t.name="" end
		if t.arg==nil then t.arg="" end

		if t.xc==nil then t.xc=conky_window.width/2 end
		if t.yc==nil then t.yc=conky_window.height/2 end
		if t.thickness ==nil then t.thickness = 10 end
		if t.radius ==nil then t.radius =conky_window.width/4 end
		if t.start_angle==nil then t.start_angle =0 end
		if t.end_angle==nil then t.end_angle=360 end
		if t.bg_colour1==nil then 
			t.bg_colour1={{0,0x00ffff,0.1},{0.5,0x00FFFF,0.5},{1,0x00FFFF,0.1}}
		end
		if t.fg_colour1==nil then
			t.fg_colour1={{0,0x00FF00,0.1},{0.5,0x00FF00,1},{1,0x00FF00,0.1}}
		end
		if t.bd_colour1==nil then
			t.bd_colour1={{0,0xFFFF00,0.5},{0.5,0xFFFF00,1},{1,0xFFFF00,0.5}}
		end
		if t.sectors==nil then t.sectors=10 end
		if t.gap_sectors==nil then t.gap_sectors=1 end 
		if t.fill_sector==nil then t.fill_sector=false end
		if t.sectors==1 then t.fill_sector=false end
		if t.border_size==nil then t.border_size=0 end
		if t.cap==nil then t.cap="p" end
		--some checks
		if t.thickness>t.radius then t.thickness=t.radius*0.1 end
		t.int_radius = t.radius-t.thickness

		--check colors tables 
		for i=1, #t.bg_colour1 do 
			if #t.bg_colour1[i]~=3 then t.bg_colour1[i]={1,0xFFFFFF,0.5} end
		end
		for i=1, #t.fg_colour1 do 
			if #t.fg_colour1[i]~=3 then t.fg_colour1[i]={1,0xFF0000,1} end
		end
		for i=1, #t.bd_colour1 do 
			if #t.bd_colour1[i]~=3 then t.bd_colour1[i]={1,0xFFFF00,1} end
		end
	
		if t.bg_colour2~=nil then
			for i=1, #t.bg_colour2 do 
				if #t.bg_colour2[i]~=3 then t.bg_colour2[i]={1,0xFFFFFF,0.5} end
			end
		end
		if t.fg_colour2~=nil then
			for i=1, #t.fg_colour2 do 
				if #t.fg_colour2[i]~=3 then t.fg_colour2[i]={1,0xFF0000,1} end
			end
		end
		if t.bd_colour2~=nil then
			for i=1, #t.bd_colour2 do 
				if #t.bd_colour2[i]~=3 then t.bd_colour2[i]={1,0xFFFF00,1} end
			end
		end 	
		
		if t.start_angle>=t.end_angle then
		 local tmp_angle=t.end_angle
		 t.end_angle= t.start_angle
		 t.start_angle = tmp_angle
		 -- print ("inversed angles")
			if t.end_angle-t.start_angle>360 and t.start_angle>0 then
				t.end_angle=360+t.start_angle
				print ("reduce angles")
			end
		
			if t.end_angle+t.start_angle>360 and t.start_angle<=0 then
				t.end_angle=360+t.start_angle
				print ("reduce angles")
			end
		
			if t.int_radius<0 then t.int_radius =0 end
			if t.int_radius>t.radius then
				local tmp_radius=t.radius
				t.radius=t.int_radius
				t.int_radius=tmp_radius
				print ("inversed radius")
			end
			if t.int_radius==t.radius then
				t.int_radius=0
				print ("int radius set to 0")
			end 
		end
		
		t.fg_colour1 = calc_delta(t.fg_colour1,t.fg_colour2)
		t.bg_colour1 = calc_delta(t.bg_colour1,t.bg_colour2)
		t.bd_colour1 = calc_delta(t.bd_colour1,t.bd_colour2)
	end
	
	--initialize table
	setup(t)
	--[[grid
	h=conky_window.height
	w=conky_window.width
	cairo_set_source_rgba(cr,1,1,1,1)
	cairo_set_line_width(cr,0.5)
	cairo_move_to(cr,0,t.yc)
	cairo_line_to(cr,w,t.yc)
	cairo_stroke(cr)
	cairo_move_to(cr,t.xc,0)
	cairo_line_to(cr,t.xc,h)
	cairo_stroke(cr)
	cairo_move_to(cr,t.xc,t.yc)
	cairo_line_to(cr,t.xc+200*math.sin(math.pi/4),t.yc-200*math.cos(math.pi/4))
	cairo_stroke(cr)
	cairo_move_to(cr,0,t.yc-t.radius)
	cairo_line_to(cr,w,t.yc-t.radius)
	cairo_stroke(cr)
	cairo_move_to(cr,0,t.yc-t.int_radius)
	cairo_line_to(cr,w,t.yc-t.int_radius)
	cairo_stroke(cr)
	cairo_move_to(cr,0,t.yc-t.gap_sectors)
	cairo_line_to(cr,w,t.yc-t.gap_sectors)
	cairo_stroke(cr)
	cairo_set_source_rgba(cr,1,0,0,0.5)
	cairo_arc(cr,t.xc,t.yc,t.radius,0,2*math.pi)
	cairo_stroke(cr)
	cairo_arc(cr,t.xc,t.yc,t.int_radius,0,2*math.pi)	
	cairo_stroke(cr)	
	cairo_set_source_rgba(cr,0,1,0,1)	
	cairo_move_to(cr,t.xc+t.gap_sectors,t.yc-t.gap_sectors)
	cairo_line_to(cr,t.xc+400*math.sin(math.pi/4),t.yc-400*math.cos(math.pi/4))
	cairo_stroke(cr)
	--END GRID
	]]
	
	--initialize cairo context
	cairo_save(cr)
	cairo_translate(cr,t.xc,t.yc)
	cairo_set_line_join (cr, CAIRO_LINE_JOIN_ROUND)
	cairo_set_line_cap (cr, CAIRO_LINE_CAP_ROUND)

	--get value
	local value = 0
	if t.name ~="" then
		value = tonumber(conky_parse(string.format('${%s %s}', t.name, t.arg)))
	else
		value = tonumber(t.arg)
	end
	if value==nil then value =0 end

	--initialize sectors
	--angle of a sector :
	angleA = ((t.end_angle-t.start_angle)/t.sectors)*math.pi/180
	--value of a sector : 
	valueA = t.max/t.sectors
	--first angle of a sector : 
	lastAngle = t.start_angle*math.pi/180


	local function draw_sector(type_arc,angle0,angle,valpc, idx)
	 
		--this function draws a portion of arc
	 	--type of arc, angle0 = strating angle, angle= angle of sector,
	 	--valpc = percentage inside the sector, idx = sctor number #
		 if type_arc=="bg" then 		--background
			 if valpc==1 then return end
		 	tcolor=t.bg_colour1
		 elseif type_arc=="fg" then	--foreground
		 	if valpc==0 then return end
		 	tcolor=t.fg_colour1
		 elseif type_arc=="bd" then	--border
		 	tcolor=t.bd_colour1
		 end 

		--angles equivalents to gap_sector
		local ext_delta=math.atan(t.gap_sectors/(2*t.radius))
		local int_delta=math.atan(t.gap_sectors/(2*t.int_radius))

		--angles of arcs
		local ext_angle=(angle-ext_delta*2)*valpc
		local int_angle=(angle-int_delta*2)*valpc

		--define colours to use for this sector
		if #tcolor==1 then 
			--plain color
			local vR,vG,vB,vA = rgba_to_r_g_b_a(tcolor[1])
			cairo_set_source_rgba(cr,vR+tcolor[1].dR*idx,
									vG+tcolor[1].dG*idx,
									vB+tcolor[1].dB*idx,
									vA+tcolor[1].dA*idx	)
		else
			--radient color
			local pat=cairo_pattern_create_radial(0,0,t.int_radius,0,0,t.radius)
			for i=1, #tcolor do
				local vP,vR,vG,vB,vA = tcolor[i][1], rgba_to_r_g_b_a(tcolor[i])
				cairo_pattern_add_color_stop_rgba (pat, 
									vP+tcolor[i].dP*idx,
									vR+tcolor[i].dR*idx,
									vG+tcolor[i].dG*idx,
									vB+tcolor[i].dB*idx,
									vA+tcolor[i].dA*idx	)
			end
			cairo_set_source (cr, pat)
			cairo_pattern_destroy(pat)
		end

		--start drawing
		 cairo_save(cr)
		--x axis is parrallel to start of sector
		cairo_rotate(cr,angle0-math.pi/2)

		local ri,re = t.int_radius ,t.radius

		--point A 
		local angle_a
	
		if t.cap == "p" then 
			angle_a = int_delta
			if t.inverse_arc and type_arc ~="bg" then
				angle_a = angle-int_angle-int_delta
			end
			if not(t.inverse_arc) and type_arc =="bg" then
				angle_a = int_delta+int_angle
			end
		else --t.cap=="r"
			angle_a = ext_delta
			if t.inverse_arc and type_arc~="bg" then
				angle_a = angle-ext_angle-ext_delta
			end
			if not(t.inverse_arc) and type_arc=="bg" then
				angle_a = ext_delta+ext_angle
			end
		end
		local ax,ay = ri*math.cos(angle_a),ri*math.sin(angle_a)


		--point B
		local angle_b = ext_delta
		if t.cap == "p" then 
			if t.inverse_arc and type_arc ~="bg" then
				angle_b = angle-ext_angle-ext_delta
			end
			if not(t.inverse_arc) and type_arc=="bg" then
				angle_b = ext_delta+ext_angle
			end
		else
			if t.inverse_arc and type_arc ~="bg" then
				angle_b = angle-ext_angle-ext_delta
			end
			if not(t.inverse_arc) and type_arc=="bg" then
				angle_b = ext_delta+ext_angle
			end
		end
		local bx,by = re*math.cos(angle_b),re*math.sin(angle_b)

		-- EXTERNAL ARC B --> C
		if t.inverse_arc then
			if type_arc=="bg" then
				b0,b1= ext_delta, angle-ext_delta-ext_angle
			else
				b0,b1= angle-ext_angle-ext_delta, angle-ext_delta
			end
		else
			if type_arc=="bg" then
				b0,b1= ext_delta+ext_angle, angle-ext_delta
			else
				b0,b1= ext_delta, ext_angle+ext_delta
			end
		end
		
		---POINT D
		local angle_c 
		if t.cap == "p" then 
			angle_d = angle-int_delta
			if t.inverse_arc and type_arc=="bg" then
				angle_d = angle-int_delta-int_angle	
			end
			if not(t.inverse_arc) and type_arc~="bg" then
				angle_d=int_delta+int_angle
			end
		else
			angle_d = angle-ext_delta
			if t.inverse_arc and type_arc=="bg" then
				angle_d =angle-ext_delta-ext_angle
			end
			if not(t.inverse_arc) and type_arc~="bg" then
				angle_d = ext_angle+ext_delta
			end
		end
		local dx,dy = ri*math.cos(angle_d),ri*math.sin(angle_d)
		
		-- INTERNAL ARC D --> A
		if t.cap=="p" then	
			if t.inverse_arc then	
				if type_arc=="bg" then
					d0,d1= angle-int_delta-int_angle,int_delta
				else
					d0,d1= angle-int_delta, angle- int_angle-int_delta
				end
			else
				if type_arc=="bg" then
					d0,d1= angle-int_delta, int_delta+int_angle
				else
					d0,d1= int_delta+int_angle, int_delta
				end
			end
		else
			if t.inverse_arc then	
				if type_arc=="bg" then	
					d0,d1= angle-ext_delta-ext_angle,ext_delta
				else
					d0,d1= angle-ext_delta, angle- ext_angle-ext_delta
				end
			else
				if type_arc=="bg" then	
					d0,d1= angle-ext_delta,ext_delta+ext_angle
				else	
					d0,d1= ext_angle+ext_delta, ext_delta
				end
			end			
		end
			
		--draw sector
		cairo_move_to(cr,ax,ay)
		cairo_line_to(cr,bx,by)
		cairo_arc(cr,0,0,re,b0,b1)
		cairo_line_to(cr,dx,dy) 
		cairo_arc_negative(cr,0,0,ri,d0,d1)
		 cairo_close_path (cr);

		--stroke or fill sector
		 if type_arc=="bd" then
		 	cairo_set_line_width(cr,t.border_size)
		 	cairo_stroke(cr)
		 else
			 cairo_fill(cr)
		 end

		 cairo_restore(cr)

	 end
	--draw sectors
	local n0,n1,n2 = 1,t.sectors,1
	if t.inverse_arc then n0,n1,n2 = t.sectors,1,-1 end
	local index = 0
	for i = n0,n1,n2 do 
		index = index +1
		local valueZ=1
		local cstA, cstB = (i-1),i
		if t.inverse_arc then cstA,cstB = (t.sectors-i), (t.sectors-i+1) end
		
		if value>valueA *cstA and value<valueA*cstB then
			if not t.fill_sector then
				valueZ = (value-valueA*cstA)/valueA
			end
		else
			if value<valueA*cstB then valueZ=0 end
		end
		
		local start_angle= lastAngle+(i-1)*angleA
		if t.foreground ~= false then 
			draw_sector("fg",start_angle,angleA,valueZ, index)
		end
		if t.background ~= false then 
			draw_sector("bg",start_angle,angleA,valueZ, i)
		end
		if t.border_size>0 then draw_sector("bd",start_angle,angleA,1, i) end
	end

	cairo_restore(cr)
end


--[[END OF RING-SECTORS WIDGET]]
function clock_hands(xc, yc, colour, alpha, show_secs, size)
	
--[[ Options (xc, yc, colour, alpha, show_secs, size):
	"xc" and "yc" are the x and y coordinates of the centre of the clock hands, in pixels, relative to the top left corner of the Conky window
	"colour" is the colour of the clock hands, in Ox33312c formate
	"alpha" is the alpha of the hands, between 0 and 1
	"show_secs" is a boolean; set to TRUE to show the seconds hand, otherwise set to FALSE
	"size" is the total size of the widget (e.g. twice the length of the minutes hand), in pixels ]]
	
	local secs,mins,hours,secs_arc,mins_arc,hours_arc
	local xh,yh,xm,ym,xs,ys

	secs=os.date("%S")
	mins=os.date("%M")
	hours=os.date("%I")

	secs_arc=(2*math.pi/60)*secs
	mins_arc=(2*math.pi/60)*mins+secs_arc/60
	hours_arc=(2*math.pi/12)*hours+mins_arc/12

	xh=xc+0.4*size*math.sin(hours_arc)
	yh=yc-0.4*size*math.cos(hours_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xh,yh)

	cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
	cairo_set_line_width(cr,5)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(colour,alpha))
	cairo_stroke(cr)

	xm=xc+0.5*size*math.sin(mins_arc)
	ym=yc-0.5*size*math.cos(mins_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xm,ym)

	cairo_set_line_width(cr,3)
	cairo_stroke(cr)

	if show_secs then
		xs=xc+0.5*size*math.sin(secs_arc)
		ys=yc-0.5*size*math.cos(secs_arc)
		cairo_move_to(cr,xc,yc)
		cairo_line_to(cr,xs,ys)

		cairo_set_line_width(cr,1)
		cairo_stroke(cr)
	end

	cairo_set_line_cap(cr,CAIRO_LINE_CAP_BUTT)
end

--[[ END CLOCK HANDS WIDGET ]]

function axis(ctx,alpha)
	cairo_set_line_width(ctx,1)
	cairo_set_source_rgba(ctx,1,0,0,alpha)
	cairo_move_to(ctx,0,0)
	cairo_line_to(ctx,150,0)
	cairo_stroke(ctx)
	cairo_set_source_rgba(ctx,0,1,0,alpha)
	cairo_move_to(ctx,0,0)
	cairo_line_to(ctx,0,150)
	cairo_stroke(ctx)
end
```

---

### Post by wlourf on 2010-09-16
Hello I like your first ring !
For the  hot-pluggable devices, in an other script "pie_chart widget" I use this script in Lua :
```
function read_df(show_media,sort_table)
    --read output of command df and return arrays of value for files systems
    --reurn array of table {file syst, "", occupied space , total space , convert to G, M, K ...}
    
    local f = io.popen("df")

    local results={}

    while true do
         local line = f:read("*l")
         if line == nil then break end
         while string.match(line,"  ") do
             line=string.gsub(line,"  "," ")
         end
        local arr_l=string.split(line," ")
        local match = string.match(arr_l[1],"/")
        
        if string.match(arr_l[1],"/") then
            if not show_media then arr_l[6]=string.gsub(arr_l[6],"/media/","",1) end
            table.insert(results,{arr_l[6],"",(arr_l[2]-arr_l[4])*1024,arr_l[2]*1024,true})
        end
    end

    f:close()
    
    if sort_table then
        --how to sort table into table?
        local flagS=true
        while flagS do
            for k=2, #results do 
                flagS=false
                if tonumber(results[1][3])>tonumber(results[2][3]) then
                    local tmpV = results[1]
                    results[1] = results[2]
                    results[2] = tmpV
                    flagS=true
                end
                if tonumber(results[k][3])<tonumber(results[k-1][3]) then
                    local tmpV = results[k-1]
                    results[k-1] = results[k]
                    results[k] = tmpV
                    flagS=true
                end
            end
        end
    end
    
    return results --array {file syst, occupied space , total space }
end
```(it only reads the return of the "df" command and send result to table_settings 
```
tableV=read_df(false,true),
```But in the script "pie_chart.lua" you can have more than one value in a single ring, like this :
```
            tableV={
                {"cpu 3","cpu","cpu1",100,"%"},
                {"cpu 2","cpu","cpu1",100,"%"},    
                {"cpu 1","cpu","cpu1",100,"%"},                            
                {"cpu 0","cpu","cpu0",100,"%"},
                {"mem","memperc","",100,"%"},        
                {"fan cpu","exec","sensors | grep fan2 | awk '{print $2}'",1500,"rpm"},
                {"temp.","exec","sensors | grep temp1 | cut -c15-16",60,"°C"},                
                },
```
Do you see the difference with the "ring-sectors" widget where you can have only one value for one ring : 
```
    name="exec",
    arg="sensors -f | grep 'temp1' | cut -c15-16",
    max=60,
```anyway, you can try to modify the ring-sectors with the read_df function but this sound a bit complicated for me :o


Link to the pie-chart widget if you are interested : [http://ubuntuforums.org/showpost.php?p=9118129&postcount=253](http://ubuntuforums.org/showpost.php?p=9118129&postcount=253).
And the output :
[IMG]http://uppix.net/8/3/b/47f3061b14989f4b8efc4d0521132.png[/IMG]

---

### Post by jo-shva on 2010-09-17
Thank You! Your scripts have been invaluable to me while trying to grasp lua...i understand some bash, not much.  Im trying to get my head around your pie_rings. 
I get this error while trying to run your scripts pie12 and pie121:
```
Conky: llua_do_call: function conky_main_pie execution failed: /home/scripts/piechart.lua:508: bad argument #1 to 'gsub' (string expected, got nil)
```

What am i missing? :confused:

---

### Post by wlourf on 2010-09-17
Well, that looks strange,
what is the output of the command "df" in a terminal ?

---

### Post by jo-shva on 2010-09-18
heres the output:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             32084760  15157888  15297084  50% /
none                   1409088       348   1408740   1% /dev
none                   1418480      1020   1417460   1% /dev/shm
none                   1418480       404   1418076   1% /var/run
none                   1418480         0   1418480   0% /var/lock
none                   1418480         0   1418480   0% /lib/init/rw
/dev/sda3               105383     66659     33103  67% /boot
/dev/sda8              2489276    174640   2188128   8% /tmp
/dev/sda7              8111460   1509780   6189596  20% /var
/dev/sda9             80937164  49836656  26989076  65% /home
/dev/sda1            162722352 113868388  48853964  70% /windows
/home/jo-shva/.Private
                      80937164  49836656  26989076  65% /home/jo-shva

```

---

### Post by wlourf on 2010-09-18
Hello, 

The problem is here :
```
/home/jo-shva/.Private
                      80937164  49836656  26989076  65% /home/jo-shva
```This partition is on two lines instead of one line, so this crash the script :(
A workaround could be, to write that :
```
            if arr_l[6] == nil then
                local line2 = f:read("*l")
                while string.match(line2,"  ") do
                     line2=string.gsub(line2,"  "," ")
                 end
                 local arr_l2=string.split(line2," ")
                 for idx=2,6 do
                    arr_l[idx]=arr_l2[idx]
                 end
            end
```just **before** theses lines (508 and 509) :
```
if not show_media then arr_l[6]=string.gsub(arr_l[6],"/media/","",1) end
table.insert(results,{arr_l[6],"",(arr_l[2]-arr_l[4])*1024,arr_l[2]*1024,true})
```With your df output, you will have that :
[IMG]http://uppix.net/5/9/e/1ed2aae0567553ef3814ae1303fbe.png[/IMG]
which is not very readable, so change the table setting for this ring with a bigger "line_space" parameter :
```
        {--CIRCLE 3 : DISK SPACE
            tableV=read_df(false,true),
            xc=580,
            yc=h - 170 ,
            radius_int=0,
            radius_ext=75,
            type_arc="r",
            proportional=true,
            first_angle=10,
            last_angle=370,
            show_text=flag_show_text,
            line_space=16,
            line_length=140,
            txt_format="&l free &n",    
            tablebg={            
                {0xFFFFFF,0},
                },
            tablefg={            
                {col0,1},
                {col1,1},
                {col2,1},
                },
        },        
```And the output is now :
[IMG]http://uppix.net/1/d/2/a3e6e4f53408bc7d6f02e9eb24f41.png[/IMG]
Well, it's not perfect, but it's a good start to tweak with the ring !

---

### Post by jo-shva on 2010-09-19
WOW!  Thank You Wlourf!  
That fixed the error. I am wondering why /home shows twice.  The second time bieng /home/jo-shva?
You rule!  that is exactly what i was looking to achieve.
:P

---

### Post by jo-shva on 2010-09-20
Also, when plugging in my 3tb external drive the pie graph becomes unreadable.  Is there a way to have that drive displayed on a separate pie?   And the question as to why /home shows twice. Once as /home and as /home/jo-shva?

---

### Post by wlourf on 2010-09-20
hello !

Why /home show twice ? It's out my knowledge sorry ! try to ask in an other thread  !

For the 3 Tb (wow!), the output should look like this (something unreadable, I agree):
[IMG]http://uppix.net/a/f/6/39128d62df7a6af3a64fe2ce13391.png[/IMG]

It's because the 3T disk id about 90 % of the sum of all yours disks, try to set the "proportional" option. to "false"
Example : 
```
        {--CIRCLE 3 : DISK SPACE
            tableV=read_df(false,true),
            radius_int=20,
            radius_ext=75,
            type_arc="r",
            proportional=true,
            first_angle=10,
            last_angle=370,
            show_text=flag_show_text,
            line_space=16,
            line_length=140,
            txt_format="&l : &v",    
            **proportional=false,**
            tablebg={            
                {0xFFFFFF,1},
                },
            tablefg={            
                {0xffFF00,1},
                {0x00FF00,1},
                },
        },
```With the same values of the above ring, the output is :
[IMG]http://uppix.net/2/7/7/c96865b2b1bfe333bb36cbc60301a.png[/IMG]

You notice the script doesn't show the Tera symbol (I have to fix that )

Hth, if you post a screenshot of your desktop, let show us !

---

### Post by Habitual on 2010-09-23
I am trying to learn some LUA stuff and I've run into a wall.

Templates I modified are:
TEXT WIDGET v1.3 by Wlourf 25/06/2010
RINGS with SECTORS widget v1.0 by wlourf (08.08.2010)

I am trying to replicate the cpu0 to cpu1 but I get identical output.

The conky [DOCs]("http://conky.sourceforge.net/variables.html") say to use cpuN but I'm stuck.

Attached are the particular files involved.

Thank you for your time.

I should specify that I have a Dual Core processor.


I think I posted prematurely. as this seems to be working...

```

text=conky_parse("${cpu cpu0} %"),
			font_name="Japan",
			font_size=14,
			h_align="c",
			bold=true,
			x=50,
			y=65,
			colour={{0,0X999999,0.5},{0.5,0x999999,1}, {1,0x999999,0.5}},

```
and
```

text=conky_parse("${cpu cpu1} %"),
			font_name="Japan",
			font_size=14,
			h_align="c",
			bold=true,
			x=50,
			y=65,
			colour={{0,0X999999,0.5},{0.5,0x999999,1}, {1,0x999999,0.5}},

```

Thanks!

---

### Post by jo-shva on 2010-09-23
Thanks again wlourf for all your help!
heres the screenshot.  I incorporated the clock and conkyForecast.  built new compass set for conkyForcast.
Cheers :popcorn:

---

### Post by wlourf on 2010-09-23
@habitual : you can check in your conky in the TEXT section, what cpu you should use
```

${cpu cpu0}
${cpu cpu1}
${cpu cpu1}
```If 3 output are the same ... I have no idea !

Edit: from doc you should start at cpu 1 :
> CPU usage in percents. For SMP machines, the CPU         number can be provided as an argument. ${cpu cpu0} is the         total usage, and ${cpu cpuX} (X >= 1) are individual         CPUs.          @jo-shva
well done :)

---

### Post by Habitual on 2010-09-23
wlourf:

So, Which method I should use to display these values?

I am currently using 
```

text=conky_parse("${cpu cpu0} %"),
text=conky_parse("${cpu cpu1} %"),

```
in the text.lua

To be honest, that that took me 4 hours to "complete" satisfactorily and I fear another ~4 hours would be necessary to use the method you suggest, even if I knew how to setup ${cpu cpu1}, ${cpu cpu2}

in the TEXT section, I'm not certain how to 'call' it from the text.lua
Edit: N/M the previous statement, I just "realized" how it's done. :D
The 'inline' method of using conky functions in text.lua seems okay for me, at this time.

I can do "pretty code" on the next rewrite, which you know is always 'just around the corner' in Conky-Land. :P

Peace. Thanks.

---

### Post by wlourf on 2010-09-23
so it works ? 4  hours is a bit long but you didn't start with a simple script ! 

in conky_parse(""), you srite the same text as if you were in your conkyrc file, even $exec with scripts or wathever (except graph I bet )!

---

### Post by Habitual on 2010-09-23
Yes, sure does.

and the recent mods...[IMG]http://i771.photobucket.com/albums/xx360/E522260/Widgets/cpu.png[/IMG]

---

### Post by Habitual on 2010-09-28
Well, it's official.
I'm writing my first LUA script for an effect that I have never seen or read about anywhere. I'd be more elaborate, but I don't want my "baby"
compromised by publicly posting the genesis of my vision. 

No imlib2 stuff, straight Cairo internals (I hope).

If you'd like to be credited with the process, I could use a mentor for the learning process.

Prepare for an onslaught of kicking and screaming, mostly by me. :D

[email]Void.RecycleBin@gmail.com[/email]
Thanks for listening. Let's hope I learn enough to start contributing regularly to the conky+Lua community.

---

### Post by wlourf on 2010-09-28
welcome in the hell of conky, habitual  !
I stay tune to watch your vision !
I guess you will add some bumped effect to the earth, like this:
[IMG]http://uppix.net/4/2/1/141d7fb8a5386eeea796b8324b88d.png[/IMG]
am I right ?

---

### Post by Habitual on 2010-09-28
wlourf:

Thanks for all your help so far.

I have managed to get 2 LUAs to work together, but not 3.
Attached is the screenshot of one of my current hacks (this is NOT the LUA that I'm writing)

Seems any attempt to *draw_text* with this configuration either draws the text and globe but no rings, or text with rings but no globe. What I can get is rings and globe but NO text. I was hoping for rings, text **AND** globe.

The globe now updates via the get_moon_earth.sh script instead of that static image I did have.

I've tried various placements of 
```

lua_load /home/JJ/Documents/Conky/Earth/rings.lua
lua_draw_hook_pre main_rings

lua_load /home/JJ/Documents/Conky/Moon/square_to_round.lua
lua_draw_hook_post main /tmp/earth/earth_image

-- MrPeachy's circle_writing LUA
lua_load /home/JJ/Documents/Conky/Earth/circle_writing.lua
lua_draw_hook_post draw_text

```

I tried various combinations of placement and I get what I have now. That's the best I can seem to do.

I tried _pre or _post on every combination. Nothing gets Text on the screen without losing 1 of the 2 (either rings or globe).

Advice or suggestions welcome.

Thank you for your time.

Edit:

I got the text on the output by using 
```

${voffset 21}${goto 266}${font DejaVu Sans Mono:size=9}MEM
${goto 266}${font DejaVu Sans Mono:size=9}CPU

```
in the rc file.

Looks cheesey, but it works, mostly. 2.png attached.

---

### Post by wlourf on 2010-09-29
Hi Habitual,


You can't have more than ONE _post and ONE _pre  call in the same conky (of course you can have both).
The workaround is to have a single _pre call which call a function in a Lua script, and this function can call all the functions you need :
```

function conky_main()
   conky_draw_text()
   conky_draw_circle()
--and so on
--you can also rename your functions whithout conky_
end
```Maybe you will have to call functions in differents files, use dofile or require or something like that to load files, I can't remember exactly !
If you use my script, you can credit me of course !:)

---

### Post by Habitual on 2010-09-29
> **wlourf said:**
> Hi Habitual,


You can't have more than ONE _post and ONE _pre  call in the same conky (of course you can have both).
The workaround is to have a single _pre call which call a function in a Lua script, and this function can call all the functions you need :
```

function conky_main()
   conky_draw_text()
   conky_draw_circle()
--and so on
--you can also rename your functions whithout conky_
end
```Maybe you will have to call functions in differents files, use dofile or require or something like that to load files, I can't remember exactly !
If you use my script, you can credit me of course !:)

Sooooooo, If I rename the functions....I tried that, but I don't remember if I renamed conky_draw_text

Work in Progress...

Psst. I don't even know your Mother! :KS

---

### Post by Habitual on 2010-09-29
Hello peeps:

Any one else using the get_moon_earth.sh script with the SQUARE_TO_ROUND WIDGET by Wlourf (07 April 2010) version 1.0.1?

I have some questions...
I have had it working in the past to update the retrieved image on a regular basis, but lately it is not updating that image.

I don't think I messed with working code, but who knows? I can't seem to stop myself sometimes, whacking out new stuff.:confused:

Thank you for your time.

---

### Post by wlourf on 2010-09-30
Yeah, after a long time of running, the image disappear, I don't know why. I don't think it's a memory leak beacause memory doesn't increase ... I have really no idea about that.
BUT I posted a workaround yesterday, this one doesn't use Lua :
[http://ubuntuforums.org/showpost.php?p=9088516&postcount=244](http://ubuntuforums.org/showpost.php?p=9088516&postcount=244)
and we can have rounded images as well.

---

### Post by Habitual on 2010-09-30
> **wlourf said:**
> Yeah, after a long time of running, the image disappear...

I noticed that also, I just restarted the widget rather than drive you mad.

Well, less than Good News. I used the code snippets from [http://ubuntuforums.org/showpost.php?p=9088516&postcount=244](http://ubuntuforums.org/showpost.php?p=9088516&postcount=244)
and the widget still died overnight.

I did NOT use larryni's script (not yet).

Bummer, back to square 1 for me.

Thanks!

---

### Post by wlourf on 2010-10-08
Hello,

is there any chance that someone can translate this code from C to Lua:

From the documentation [http://www.dynaset.org/dogusanh/luacairo.html](http://www.dynaset.org/dogusanh/luacairo.html) 
```

 * Here is sample code for iterating through a #cairo_path_t:
 *
 * 
 *      int i;
 *      cairo_path_t *path;
 *      cairo_path_data_t *data;
 *  
 *      path = cairo_copy_path (cr);
 *  
 *      for (i=0; i < path->num_data; i += path->data[i].header.length) {
 *          data = &path->data[i];
 *          switch (data->header.type) {
 *          case CAIRO_PATH_MOVE_TO:
 *              do_move_to_things (data[1].point.x, data[1].point.y);
 *              break;
 *          case CAIRO_PATH_LINE_TO:
 *              do_line_to_things (data[1].point.x, data[1].point.y);
 *              break;
 *          case CAIRO_PATH_CURVE_TO:
 *              do_curve_to_things (data[1].point.x, data[1].point.y,
 *                                  data[2].point.x, data[2].point.y,
 *                                  data[3].point.x, data[3].point.y);
 *              break;
 *          case CAIRO_PATH_CLOSE_PATH:
 *              do_close_path_things ();
 *              break;
 *          }
 *      }
 *      cairo_path_destroy (path);
```what I've done so far is to retrieve the cairo_path_length with .numdata and cairo_path_data_t with .data :
```
    path=cairo_copy_path(cr)
    print ("status,data,num_data",path.status, path.data, path.num_data)
```but how to loop through the cairo_path_data_t like in C ??

I can't find headers or things like this, if someone can help! thanks :)

---

### Post by Habitual on 2010-10-11
> **wlourf said:**
> Hello,

is there any chance that someone can translate this code from C to Lua:

From the documentation [http://www.dynaset.org/dogusanh/luacairo.html](http://www.dynaset.org/dogusanh/luacairo.html) 
```

 * Here is sample code for iterating through a #cairo_path_t:
 *
 * 
 *      int i;
 *      cairo_path_t *path;
 *      cairo_path_data_t *data;
 *  
 *      path = cairo_copy_path (cr);
 *  
 *      for (i=0; i < path->num_data; i += path->data[i].header.length) {
 *          data = &path->data[i];
 *          switch (data->header.type) {
 *          case CAIRO_PATH_MOVE_TO:
 *              do_move_to_things (data[1].point.x, data[1].point.y);
 *              break;
 *          case CAIRO_PATH_LINE_TO:
 *              do_line_to_things (data[1].point.x, data[1].point.y);
 *              break;
 *          case CAIRO_PATH_CURVE_TO:
 *              do_curve_to_things (data[1].point.x, data[1].point.y,
 *                                  data[2].point.x, data[2].point.y,
 *                                  data[3].point.x, data[3].point.y);
 *              break;
 *          case CAIRO_PATH_CLOSE_PATH:
 *              do_close_path_things ();
 *              break;
 *          }
 *      }
 *      cairo_path_destroy (path);
```what I've done so far is to retrieve the cairo_path_length with .numdata and cairo_path_data_t with .data :
```
    path=cairo_copy_path(cr)
    print ("status,data,num_data",path.status, path.data, path.num_data)
```but how to loop through the cairo_path_data_t like in C ??

I can't find headers or things like this, if someone can help! thanks :)

I found plenty of C references and LUA at [http://zetcode.com/tutorials/cairographicstutorial](http://zetcode.com/tutorials/cairographicstutorial) that may help.
```

#include <cairo.h>
#include <gtk/gtk.h>
#include <math.h>

```
seem prevalent there.

---

### Post by wlourf on 2010-10-18
Thanks habitual, but I am looking for headers in the cairo_path_t structure !
Still searching :(

---

### Post by 42dorian on 2010-12-02
I Pose a Challenge To You!

Anyone who can write a script I can add to my Conky, a simple gauge that fills up the closer to a maximum total data use you get.  Should probably call the data from vnstat, compare it to a number of maximum data given, and output a gauge graphic of some sort.

Waddaya Say folks?  Doable?  ('Cause I haven't a clue how.)

*EDIT*...I went to sleep and woke up with a epiphany... can I load [that]("http://ubuntuforums.org/showthread.php?p=9373750#post9373750") script, call it using the "${luagauge}" command, and pass it the monthly result of vnstat instead of the interface?

At this point, I'm just not sure which thread to ask this one in... it's Conky, without a doubt. But it's a very tiny lua inside of a conky, so I don't know.

---

### Post by vickoxy on 2010-12-13
Hi,
i need to draw three little backgrounds in one conky with lua. I found this script from londonaly which works fine, but have no idea how to move them up and down. Resizing works fine, if i copy them three times in same lua script i have three background areas, but the all begin at the same place-up-left corner. So, i need to replace the to cover certain areas in my conky. Basically, there is picture down of that what i want to achieve (i use now in gimp made pictures, but lua draws background better).

anyone can help here?


```
--[[
Background by londonali1010 (2009)
This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.
To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
    lua_load ~/scripts/draw_bg.lua
    lua_draw_hook_pre draw_bg
Changelog:
+ v1.0 -- Original release (07.10.2009)
]]
-- Change these settings to affect your background.
-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.
corner_r=35
-- Set the colour and transparency (alpha) of your background.
bg_colour=0xFFFFFF
bg_alpha=0.0
require 'cairo'
function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
function conky_draw_bg()
    if conky_window==nil then return end
    local w=conky_window.width
    local h=conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
    cr=cairo_create(cs)
    
    cairo_move_to(cr,corner_r,0)
    cairo_line_to(cr,w-corner_r,0)
    cairo_curve_to(cr,w,0,w,0,w,corner_r)
    cairo_line_to(cr,w,h-corner_r)
    cairo_curve_to(cr,w,h,w,h,w-corner_r,h)
    cairo_line_to(cr,corner_r,h)
    cairo_curve_to(cr,0,h,0,h,0,h-corner_r)
    cairo_line_to(cr,0,corner_r)
    cairo_curve_to(cr,0,0,0,0,corner_r,0)
    cairo_close_path(cr)
    
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
    cairo_fill(cr)
end
```

---

### Post by 42dorian on 2010-12-13
> **vickoxy said:**
> Hi,
i need to draw three little backgrounds in one conky with lua. I found this script from londonaly which works fine, but have no idea how to move them up and down. Resizing works fine, if i copy them three times in same lua script i have three background areas, but the all begin at the same place-up-left corner. So, i need to replace the to cover certain areas in my conky. Basically, there is picture down of that what i want to achieve (i use now in gimp made pictures, but lua draws background better).

anyone can help here?


```
--[[
Background by londonali1010 (2009)
This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.
To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
    lua_load ~/scripts/draw_bg.lua
    lua_draw_hook_pre draw_bg
Changelog:
+ v1.0 -- Original release (07.10.2009)
]]
-- Change these settings to affect your background.
-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.
corner_r=35
-- Set the colour and transparency (alpha) of your background.
bg_colour=0xFFFFFF
bg_alpha=0.0
require 'cairo'
function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
function conky_draw_bg()
    if conky_window==nil then return end
    local w=conky_window.width
    local h=conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
    cr=cairo_create(cs)
    
    cairo_move_to(cr,corner_r,0)
    cairo_line_to(cr,w-corner_r,0)
    cairo_curve_to(cr,w,0,w,0,w,corner_r)
    cairo_line_to(cr,w,h-corner_r)
    cairo_curve_to(cr,w,h,w,h,w-corner_r,h)
    cairo_line_to(cr,corner_r,h)
    cairo_curve_to(cr,0,h,0,h,0,h-corner_r)
    cairo_line_to(cr,0,corner_r)
    cairo_curve_to(cr,0,0,0,0,corner_r,0)
    cairo_close_path(cr)
    
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
    cairo_fill(cr)
end
```


This line looks like it's the key to moving the image.

```

   cairo_move_to(cr,corner_r,0)

```

---

### Post by vickoxy on 2010-12-14
> **42dorian said:**
> This line looks like it's the key to moving the image.

```

   cairo_move_to(cr,corner_r,0)

```

I tried, but still nothing...

---

### Post by wlourf on 2010-12-14
> **vickoxy said:**
> I tried, but still nothing...
Before the line[FONT=monospace]
[/FONT]```
cairo_move_to(cr,corner_r,0)
```[FONT=monospace] 
add a translation of the drawing surface with :
[/FONT]```
cairo_translate(cr,0,100)
```
here, for a 100 pixels translation on the y axis, this should work !
[FONT=monospace]
[/FONT]

---

### Post by vickoxy on 2010-12-18
> **wlourf said:**
> Before the line[FONT=monospace]
[/FONT]```
cairo_move_to(cr,corner_r,0)
```[FONT=monospace] 
add a translation of the drawing surface with :
[/FONT]```
cairo_translate(cr,0,100)
```
here, for a 100 pixels translation on the y axis, this should work !
[FONT=monospace]
[/FONT]

Hi and thanks-almost there... I can really move now the background to the bottom, but still can not split it in three areas. I tried to copy in the same lua script the backround code and to give them different size, but have no idea how to cut the bottom part of background. Any idea?

P.S.
i tried to copy the lua script and changed the size, but there is no effect. The second lua script doesn´t draw anything. My conky lines are:

lua_load ~/scripts/draw_bg.lua
**lua_load ~/scripts/draw_bg1.lua**
lua_draw_hook_pre draw_bg

---

### Post by wlourf on 2010-12-18
> **vickoxy said:**
> Hi and thanks-almost there... I can really move now the background to the bottom, but still can not split it in three areas. I tried to copy in the same lua script the backround code and to give them different size, but have no idea how to cut the bottom part of background. Any idea?

P.S.
i tried to copy the lua script and changed the size, but there is no effect. The second lua script doesn´t draw anything. My conky lines are:

lua_load ~/scripts/draw_bg.lua
**lua_load ~/scripts/draw_bg1.lua**
lua_draw_hook_pre draw_bg

Hi, 
Yes, londonali's script is not for multiples boxes, so just for one box, you can set the height of the box with (for 100 pixels)
```
local h=100
```instead of 
```
local h=conky_window.height
```You give me an idea for writing a multiple background script, it starts well :
[[IMG]http://uppix.com/t-multiple_bg4d0ca2f30007d403.png[/IMG]]("http://uppix.com/s-multiple_bg4d0ca2f30007d403-png.htm")
i will post it in a few days.

Now, if you want to call multiple Lua scripts, use one line to load multiple files:
```
lua_load script1 script2
```see : [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

BUT you can use only one "lua_draw_hook_pre" in your conkyrc and only ONE "lua_draw_hook_post", so you can call 2 functions. But the easiest way is to call one function which call others functions, but you have to tweak a little bit with Lua
```
function conky_main()
     draw_bg1()
     draw_bg2()
     draw_bg3()
end

```hth !

---

### Post by vickoxy on 2010-12-18
> **wlourf said:**
> Hi, 
Yes, londonali's script is not for multiples boxes, so just for one box, you can set the height of the box with (for 100 pixels)
```
local h=100
```instead of 
```
local h=conky_window.height
```You give me an idea for writing a multiple background script, it starts well :
[[IMG]http://uppix.com/t-multiple_bg4d0ca2f30007d403.png[/IMG]]("http://uppix.com/s-multiple_bg4d0ca2f30007d403-png.htm")
i will post it in a few days.

Now, if you want to call multiple Lua scripts, use one line to load multiple files:
```
lua_load script1 script2
```see : [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

BUT you can use only one "lua_draw_hook_pre" in your conkyrc and only ONE "lua_draw_hook_post", so you can call 2 functions. But the easiest way is to call one function which call others functions, but you have to tweak a little bit with Lua
```
function conky_main()
     draw_bg1()
     draw_bg2()
     draw_bg3()
end

```hth !

Please, post your solution-i am for now happy with my one background solution, but for the future i would love to see multiple backgrounds.

Thanks :popcorn:

---

### Post by jo-shva on 2010-12-18
I am also very interested in how to use 3 or more lua scripts within one conky!  I haven't been able to figure it out.  
Looking forward to your post!
Thanks

---

### Post by wlourf on 2010-12-18
I am working on it :p

but if you are in a hurry you can try to tweak with my bargraph widget : a bargraph is just a box but more sophisticated, mines have no rounded corners but you can draw fancy boxes with it :
[[IMG]http://uppix.com/t-bargraph4d0d29060007d640.png[/IMG]]("http://uppix.com/s-bargraph4d0d29060007d640-png.htm")
For the above image, I used this script (has to be called with  "lua_draw_hook_pre main_bars"):
```


--[[ BARGRAPH WIDGET
    v2.0 by wlourf (12.07.2010)
    this widget draws a bargraph with differents effects 
    http://u-scripts.blogspot.com/2010/07/bargraph-widget.html
    
    
Parameters are :
3 parameters are mandatory
name    - the name of the conky variable to display, for example for {$cpu cpu0}, just write name="cpu"
arg        - the argument of the above variable, for example for {$cpu cpu0}, just write arg="cpu0"
          arg can be a numericla value if name=""
max        - the maximum value the above variable can reach, for example for {$cpu cpu0}, just write  max=100
    
Optional parameters:
x,y        - coordinates of the starting point of the bar, default = middle of the conky window
cap        - end of cap line, ossibles values are r,b,s (for round, butt, square), default="b"
          http://www.cairographics.org/samples/set_line_cap/
angle    - angle of rotation of the bar in degress, default = 0 (i.e. a vertical bar)
          set to 90 for an horizontal bar
skew_x    - skew bar around x axis, défaut = 0
skew_y    - skew bar around y axis, défaut = 0
blocks  - number of blocks to display for a bar (values >0) , default= 10
height    - height of a block, default=10 pixels
width    - width of a block, default=20 pixels
space    - space between 2 blocks, default=2 pixels
angle_bar    - this angle is used to draw a bar on a circular way (ok, this is no more a bar !) default=0
radius        - for cicular bars, internal radius, default=0
              with radius, parameter width has no more effect.

Colours below are defined into braces {colour in hexadecimal, alpha}
fg_colour    - colour of a block ON, default= {0x00FF00,1}
bg_colour    - colour of a block OFF, défaut = {0x00FF00,0.5}
alarm        - threshold, values after this threshold will use alarm_colour colour , default=max
alarm_colour - colour of a block greater than alarm, default=fg_colour
smooth        - (true or false), create a gradient from fg_colour to bg_colour, default=false 
mid_colour    - colours to add to gradient, with this syntax {position into the gradient (0 to1), colour hexa, alpha}
              for example, this table {{0.25,0xff0000,1},{0.5,0x00ff00,1},{0.75,0x0000ff,1}} will add
              3 colurs to gradient created by fg_colour and alarm_colour, default=no mid_colour
led_effect    - add LED effects to each block, default=no led_effect
              if smooth=true, led_effect is not used
              possibles values : "r","a","e" for radial, parallelel, perdendicular to the bar (just try!)
              led_effect has to be used with theses colours :
fg_led        - middle colour of a block ON, default = fg_colour
bg_led        - middle colour of a block OFF, default = bg_colour
alarm_led    - middle colour of a block > ALARM,  default = alarm_colour

reflection parameters, not avaimable for circular bars
reflection_alpha    - add a reflection effect (values from 0 to 1) default = 0 = no reflection
                      other values = starting opacity
reflection_scale    - scale of the reflection (default = 1 = height of text)
reflection_length   - length of reflection, define where the opacity will be set to zero
                      calues from 0 to 1, default =1
reflection            - position of reflection, relative to a vertical bar, default="b"
                      possibles values are : "b","t","l","r" for bottom, top, left, right


v1.0 (10 Feb. 2010) original release
v1.1 (13 Feb. 2010) numeric values can be passed instead conky stats with parameters name="", arg = numeric_value    
v1.2 (28 Feb. 2010) just renamed the widget to bargraph
v1.3 (03 March 2010) added parameters radius & angle_bar to draw the bar in a circular way
v2.0 (12 Jul. 2010) rewrite script + add reflection effects and parameters are now set into tables
]]

require 'cairo'

----------------START OF PARAMETERS ----------
function conky_main_bars()
    bars_settings={
        {
            name="",
            arg=1,
            max=1,
            fg_colour={0x00ffff,1},
            x=10,y=10,
            blocks=1,
            height=200,width=100,
            angle=90,
            cap="r"
        },    



        {
            name="",
            arg=1,
            max=1,
            alarm=0.5,
            fg_colour={0x00ff00,1},
            alarm_colour={0xff0000,1},
            x=70,y=130,
            blocks=1,
            height=190,width=50,
            smooth=true,
            angle=90,
            mid_colour={{0.33,0x0000FF,1},{0.66,0xffff00,1}}

        },    

        {
            name="",
            arg=1,
            max=1,
            alarm=50,
            bg_colour={0x00ff00,0.25},
            fg_colour={0x00ff00,1},
            alarm_colour={0xff0000,1},
            x=10,y=300,
            blocks=1,
            height=100,width=100,
            smooth=true,
            mid_colour={{0.5,0xffff00,1}}

        },    


        {
            name="",
            arg=1,
            max=1,
            bg_colour={0x00ff33,0},
            fg_colour={0xffff00,0},
            bg_led={0x00ff33,0.5},
            fg_led={0xffff00,1},
            led_effect="r",
            blocks=1,--20,
            x=150,
            y=200,
            height=150,--,
            width=40,
            angle=90,
            led_effect="e",
            space=1,
        },    
        
        
    }
    
-----------END OF PARAMETERS--------------


    
    if conky_window == nil then return end
    
    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    
    cr = cairo_create(cs)    
    --prevent segmentation error when reading cpu state
    if tonumber(conky_parse('${updates}'))>3 then
        for i in pairs(bars_settings) do
            
            draw_multi_bar_graph(bars_settings[i])
            
        end
    end
    cairo_destroy(cr)
    cairo_surface_destroy(cs)

end



function draw_multi_bar_graph(t)
    cairo_save(cr)
    --check values
    if t.name==nil and t.arg==nil then 
        print ("No input values ... use parameters 'name' with 'arg' or only parameter 'arg' ") 
        return
    end
    if t.max==nil then
        print ("No maximum value defined, use 'max'")
        return
    end
    if t.name==nil then t.name="" end
    if t.arg==nil then t.arg="" end

    --set default values    
    if t.x == nil        then t.x = conky_window.width/2 end
    if t.y == nil        then t.y = conky_window.height/2 end
    if t.blocks == nil    then t.blocks=10 end
    if t.height == nil    then t.height=10 end
    if t.angle == nil     then t.angle=0 end
    t.angle = t.angle*math.pi/180
    --line cap style
    if t.cap==nil        then t.cap = "b" end
    local cap="b"
    for i,v in ipairs({"s","r","b"}) do 
        if v==t.cap then cap=v end
    end
    delta=0
    if t.cap=="r" or t.cap=="s" then delta = t.height end
    if cap=="s" then     cap = CAIRO_LINE_CAP_SQUARE
    elseif cap=="r" then
        cap = CAIRO_LINE_CAP_ROUND
    elseif cap=="b" then
        cap = CAIRO_LINE_CAP_BUTT
    end
    --end line cap style
    --if t.led_effect == nil    then t.led_effect="r" end
    if t.width == nil    then t.width=20 end
    if t.space == nil    then t.space=2 end
    if t.radius == nil    then t.radius=0 end
    if t.angle_bar == nil    then t.angle_bar=0 end
    t.angle_bar = t.angle_bar*math.pi/360 --halt angle
    
    --colours
    if t.bg_colour == nil     then t.bg_colour = {0x00FF00,0.5} end
    if #t.bg_colour~=2         then t.bg_colour = {0x00FF00,0.5} end
    if t.fg_colour == nil     then t.fg_colour = {0x00FF00,1} end
    if #t.fg_colour~=2         then t.fg_colour = {0x00FF00,1} end
    if t.alarm_colour == nil     then t.alarm_colour = t.fg_colour end
    if #t.alarm_colour~=2         then t.alarm_colour = t.fg_colour end

    if t.mid_colour ~= nil then    
        for i=1, #t.mid_colour do    
            if #t.mid_colour[i]~=3 then 
                print ("error in mid_color table")
                t.mid_colour[i]={1,0xFFFFFF,1} 
            end
        end
    end
    
    if t.bg_led ~= nil and #t.bg_led~=2    then t.bg_led = t.bg_colour end
    if t.fg_led ~= nil and #t.fg_led~=2    then t.fg_led = t.fg_colour end
    if t.alarm_led~= nil and #t.alarm_led~=2 then t.alarm_led = t.fg_led end
    
    if t.led_effect~=nil then
        if t.bg_led == nil then t.bg_led = t.bg_colour end
        if t.fg_led == nil     then t.fg_led = t.fg_colour end
        if t.alarm_led == nil  then t.alarm_led = t.fg_led end
    end
    

    if t.alarm==nil then t.alarm = t.max end --0.8*t.max end
    if t.smooth == nil then t.smooth = false end

    if t.skew_x == nil then 
        t.skew_x=0 
    else
        t.skew_x = math.pi*t.skew_x/180    
    end
    if t.skew_y == nil then 
        t.skew_y=0
    else
        t.skew_y = math.pi*t.skew_y/180    
    end
    
    if t.reflection_alpha==nil then t.reflection_alpha=0 end
    if t.reflection_length==nil then t.reflection_length=1 end
    if t.reflection_scale==nil then t.reflection_scale=1 end
    
    --end of default values
    

     local function rgb_to_r_g_b(col_a)
        return ((col_a[1] / 0x10000) % 0x100) / 255., ((col_a[1] / 0x100) % 0x100) / 255., (col_a[1] % 0x100) / 255., col_a[2]
    end
    
    
    --functions used to create patterns

    local function create_smooth_linear_gradient(x0,y0,x1,y1)
        local pat = cairo_pattern_create_linear (x0,y0,x1,y1)
        cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
        cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
        if t.mid_colour ~=nil then
            for i=1, #t.mid_colour do
                cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
            end
        end
        return pat
    end

    local function create_smooth_radial_gradient(x0,y0,r0,x1,y1,r1)
        local pat =  cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
        cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
        cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
        if t.mid_colour ~=nil then
            for i=1, #t.mid_colour do
                cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
            end
        end
        return pat
    end
    
    local function create_led_linear_gradient(x0,y0,x1,y1,col_alp,col_led)
        local pat = cairo_pattern_create_linear (x0,y0,x1,y1) ---delta, 0,delta+ t.width,0)
        cairo_pattern_add_color_stop_rgba (pat, 0.0, rgb_to_r_g_b(col_alp))
        cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
        cairo_pattern_add_color_stop_rgba (pat, 1.0, rgb_to_r_g_b(col_alp))
        return pat
    end

    local function create_led_radial_gradient(x0,y0,r0,x1,y1,r1,col_alp,col_led,mode)
        local pat = cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
        if mode==3 then
            cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_alp))                
            cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
            cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))                
        else
            cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_led))
            cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))                
        end
        return pat
    end






    local function draw_single_bar()
        --this fucntion is used for bars with a single block (blocks=1) but 
        --the drawing is cut in 3 blocks : value/alarm/background
        --not zvzimzblr for circular bar
        local function create_pattern(col_alp,col_led,bg)
            local pat
            
            if not t.smooth then
                if t.led_effect=="e" then
                    pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
                elseif t.led_effect=="a" then
                    pat = create_led_linear_gradient (t.width/2, 0,t.width/2,-t.height,col_alp,col_led)
                elseif  t.led_effect=="r" then
                    pat = create_led_radial_gradient (t.width/2, -t.height/2, 0, t.width/2,-t.height/2,t.height/1.5,col_alp,col_led,2)
                else
                    pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
                end
            else
                if bg then
                    pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
                else
                    pat = create_smooth_linear_gradient(t.width/2, 0, t.width/2,-t.height)
                end
            end
            return pat
        end
        
        local y1=-t.height*pct/100
        local y2=nil
        if pct>(100*t.alarm/t.max) then 
            y1 = -t.height*t.alarm/100
            y2 = -t.height*pct/100
            if t.smooth then y1=y2 end
        end
        
        if t.angle_bar==0 then
        
            --block for fg value
            pat = create_pattern(t.fg_colour,t.fg_led,false)
            cairo_set_source(cr,pat)
            cairo_rectangle(cr,0,0,t.width,y1)
            cairo_fill(cr)
        
            -- block for alarm value            
            if not t.smooth and y2 ~=nil then 
                pat = create_pattern(t.alarm_colour,t.alarm_led,false)
                cairo_set_source(cr,pat)
                cairo_rectangle(cr,0,y1,t.width,y2-y1)
                cairo_fill(cr)
                y3=y2
            else
                y2,y3=y1,y1
            end
            -- block for bg value
            cairo_rectangle(cr,0,y2,t.width,-t.height-y3)
            pat = create_pattern(t.bg_colour,t.bg_led,true)
            cairo_set_source(cr,pat)
            cairo_pattern_destroy(pat)
            cairo_fill(cr)
        end        
    end  --end single bar
    





    local function draw_multi_bar()
        --function used for bars with 2 or more blocks
        for pt = 1,t.blocks do 
            --set block y
            local y1 = -(pt-1)*(t.height+t.space)
            local light_on=false
            
            --set colors
            local col_alp = t.bg_colour
            local col_led = t.bg_led
            if pct>=(100/t.blocks) or pct>0 then --ligth on or not the block
                if pct>=(pcb*(pt-1))  then 
                    light_on = true
                    col_alp = t.fg_colour
                    col_led = t.fg_led
                    if pct>=(100*t.alarm/t.max) and (pcb*pt)>(100*t.alarm/t.max) then 
                        col_alp = t.alarm_colour 
                        col_led = t.alarm_led 
                    end
                end
            end

            --set colors
            --have to try to create gradients outside the loop ?
            local pat 
            
            if not t.smooth then
                if t.angle_bar==0 then
                    if t.led_effect=="e" then
                        pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
                    elseif t.led_effect=="a" then
                        pat = create_led_linear_gradient (t.width/2, -t.height/2+y1,t.width/2,0+t.height/2+y1,col_alp,col_led)                    
                    elseif  t.led_effect=="r" then
                        pat = create_led_radial_gradient (t.width/2, y1, 0, t.width/2,y1,t.width/1.5,col_alp,col_led,2)    
                    else
                        pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
                    end
                else
                     if t.led_effect=="a"  then
                         pat = create_led_radial_gradient (0, 0, t.radius+(t.height+t.space)*(pt-1),
                                                         0, 0, t.radius+(t.height+t.space)*(pt),                         
                                             col_alp,col_led,3)    
                    else
                        pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))                    
                    end
                    
                end
            else
                
                if light_on then
                    if t.angle_bar==0 then
                        pat = create_smooth_linear_gradient(t.width/2, t.height/2, t.width/2,-(t.blocks-0.5)*(t.height+t.space))
                    else
                        pat = create_smooth_radial_gradient(0, 0, (t.height+t.space),  0,0,(t.blocks+1)*(t.height+t.space),2)
                    end
                else        
                    pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
                end
            end
            cairo_set_source (cr, pat)
            cairo_pattern_destroy(pat)

            --draw a block
            if t.angle_bar==0 then
                cairo_move_to(cr,0,y1)
                cairo_line_to(cr,t.width,y1)
            else        
                cairo_arc( cr,0,0,
                    t.radius+(t.height+t.space)*(pt)-t.height/2,
                     -t.angle_bar -math.pi/2 ,
                     t.angle_bar -math.pi/2)
            end
            cairo_stroke(cr)
        end    
    end
    
    
    
    
    local function setup_bar_graph()
        --function used to retrieve the value to display and to set the cairo structure
        if t.blocks ~=1 then t.y=t.y-t.height/2 end
        
        local value = 0
        if t.name ~="" then
            value = tonumber(conky_parse(string.format('${%s %s}', t.name, t.arg)))
        else
            value = tonumber(t.arg)
        end

        if value==nil then value =0 end
        
        pct = 100*value/t.max
        pcb = 100/t.blocks
        
        cairo_set_line_width (cr, t.height)
        cairo_set_line_cap  (cr, cap)
        cairo_translate(cr,t.x,t.y)
        cairo_rotate(cr,t.angle)

        local matrix0 = cairo_matrix_t:create()
        cairo_matrix_init (matrix0, 1,t.skew_y,t.skew_x,1,0,0)
        cairo_transform(cr,matrix0)

    
        
        --call the drawing function for blocks
        if t.blocks==1 and t.angle_bar==0 then
            draw_single_bar()
            if t.reflection=="t" or t.reflection=="b" then cairo_translate(cr,0,-t.height) end
        else
            draw_multi_bar()
        end

        --dot for reminder
        --[[
        if t.blocks ~=1 then
            cairo_set_source_rgba(cr,1,0,0,1)
            cairo_arc(cr,0,t.height/2,3,0,2*math.pi)
            cairo_fill(cr)
        else
            cairo_set_source_rgba(cr,1,0,0,1)
            cairo_arc(cr,0,0,3,0,2*math.pi)
            cairo_fill(cr)
        end
]]
        --call the drawing function for reflection and prepare the mask used        
        if t.reflection_alpha>0 and t.angle_bar==0 then
            local pat2
            local matrix1 = cairo_matrix_t:create()
            if t.angle_bar==0 then
                pts={-delta/2,(t.height+t.space)/2,t.width+delta,-(t.height+t.space)*(t.blocks)}
                if t.reflection=="t" then
                    cairo_matrix_init (matrix1,1,0,0,-t.reflection_scale,0,-(t.height+t.space)*(t.blocks-0.5)*2*(t.reflection_scale+1)/2)
                    pat2 = cairo_pattern_create_linear (t.width/2,-(t.height+t.space)*(t.blocks),t.width/2,(t.height+t.space)/2)
                elseif t.reflection=="r" then
                    cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,delta+2*t.width,0)
                    pat2 = cairo_pattern_create_linear (delta/2+t.width,0,-delta/2,0)
                elseif t.reflection=="l" then
                    cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,-delta,0)
                    pat2 = cairo_pattern_create_linear (-delta/2,0,delta/2+t.width,-0)
                else --bottom
                    cairo_matrix_init (matrix1,1,0,0,-1*t.reflection_scale,0,(t.height+t.space)*(t.reflection_scale+1)/2)
                    pat2 = cairo_pattern_create_linear (t.width/2,(t.height+t.space)/2,t.width/2,-(t.height+t.space)*(t.blocks))
                end
            end
            cairo_transform(cr,matrix1)

            if t.blocks==1 and t.angle_bar==0 then
                draw_single_bar()
                cairo_translate(cr,0,-t.height/2) 
            else
                draw_multi_bar()
            end
            
            
            cairo_set_line_width(cr,0.01)
            cairo_pattern_add_color_stop_rgba (pat2, 0,0,0,0,1-t.reflection_alpha)
            cairo_pattern_add_color_stop_rgba (pat2, t.reflection_length,0,0,0,1)
            if t.angle_bar==0 then
                cairo_rectangle(cr,pts[1],pts[2],pts[3],pts[4])
            end
            cairo_clip_preserve(cr)
            cairo_set_operator(cr,CAIRO_OPERATOR_CLEAR)
            cairo_stroke(cr)
            cairo_mask(cr,pat2)
            cairo_pattern_destroy(pat2)
            cairo_set_operator(cr,CAIRO_OPERATOR_OVER)
            
        end --reflection
        
        
    end --setup_bar_graph()

    
    --start here !
    setup_bar_graph()
    cairo_restore(cr)
end

```Full script and examples and readme can be download on [deviantArt]("http://wlourf.deviantart.com/art/Bargraph-Widget-for-Conky-1-153733823")
but the muliple boxes script will be more simple !

---

### Post by olgmen on 2010-12-19
my version backgraund.lua

[HTML]--[[ backgraund.lua by olgmen 16.11.2010


lua_load /path/to/the/lua/script/backgraund.lua
lua_draw_hook_pre draw_backgraund

]]
require 'cairo'

function conky_draw_backgraund()


backgraund_settings={

{
bg_colour = {{0, 0x31489c, 0.5},{0.5, 0x9c5930, 0.75},{1, 0x889c30, 0.3}},
},

}

    if conky_window==nil then return end

    local cs=cairo_xlib_surface_create(conky_window.display,
        conky_window.drawable, 
        conky_window.visual, conky_window.width, conky_window.height)
    cr=cairo_create(cs)

    for i,v in pairs(backgraund_settings) do
        display_background(v)
    end

    cairo_destroy(cr)

end
-- ------------------------------------------------------------
function display_background(t)

    if t.x            == nil then t.x = 0 end
    if t.y            == nil then t.y = 0 end
    if t.width        == nil then t.width = conky_window.width end
    if t.height        == nil then t.height = conky_window.height end
    if t.radius        == nil then t.radius = (t.width+t.height)/2*0.04 end
    if t.orientation    == nil then t.orientation = "ww" end

    if t.bg_colour == nil then
        t.bg_colour = {{0, 0x00ffff, 0.1},{0.5, 0x00FFFF, 0.5},{1, 0x00FFFF, 0.1}}
    end

    local degrees = math.pi / 180.0

    cairo_new_sub_path (cr)

    cairo_arc (cr, t.x + t.width - t.radius, t.y + t.radius, t.radius, -90 * degrees, 0 * degrees)
    cairo_arc (cr, t.x + t.width - t.radius, t.y + t.height - t.radius, t.radius, 0 * degrees, 90 * degrees)
    cairo_arc (cr, t.x + t.radius, t.y + t.height - t.radius, t.radius, 90 * degrees, 180 * degrees)
    cairo_arc (cr, t.x + t.radius, t.y + t.radius, t.radius, 180 * degrees, 270 * degrees)

    cairo_close_path (cr)


        if #t.bg_colour == 1 then 
        cairo_set_source_rgba(cr,rgb_to_r_g_b2(t.bg_colour[1]))
    else
        local pat
        local pts=linear_orientation_bg(t)
        pat = cairo_pattern_create_linear (pts[1], pts[2], pts[3], pts[4])

        for i=1, #t.bg_colour do
            cairo_pattern_add_color_stop_rgba (pat, t.bg_colour[i][1], rgb_to_r_g_b2(t.bg_colour[i]))
        end

        cairo_set_source (cr, pat)
        cairo_fill (cr)
        cairo_pattern_destroy(pat)
    end
end[/HTML]

---

### Post by vickoxy on 2010-12-19
> **olgmen said:**
> my version backgraund.lua

[HTML]--[[ backgraund.lua by olgmen 16.11.2010


lua_load /path/to/the/lua/script/backgraund.lua
lua_draw_hook_pre draw_backgraund

]]
require 'cairo'

function conky_draw_backgraund()


backgraund_settings={

{
bg_colour = {{0, 0x31489c, 0.5},{0.5, 0x9c5930, 0.75},{1, 0x889c30, 0.3}},
},

}

    if conky_window==nil then return end

    local cs=cairo_xlib_surface_create(conky_window.display,
        conky_window.drawable, 
        conky_window.visual, conky_window.width, conky_window.height)
    cr=cairo_create(cs)

    for i,v in pairs(backgraund_settings) do
        display_background(v)
    end

    cairo_destroy(cr)

end
-- ------------------------------------------------------------
function display_background(t)

    if t.x            == nil then t.x = 0 end
    if t.y            == nil then t.y = 0 end
    if t.width        == nil then t.width = conky_window.width end
    if t.height        == nil then t.height = conky_window.height end
    if t.radius        == nil then t.radius = (t.width+t.height)/2*0.04 end
    if t.orientation    == nil then t.orientation = "ww" end

    if t.bg_colour == nil then
        t.bg_colour = {{0, 0x00ffff, 0.1},{0.5, 0x00FFFF, 0.5},{1, 0x00FFFF, 0.1}}
    end

    local degrees = math.pi / 180.0

    cairo_new_sub_path (cr)

    cairo_arc (cr, t.x + t.width - t.radius, t.y + t.radius, t.radius, -90 * degrees, 0 * degrees)
    cairo_arc (cr, t.x + t.width - t.radius, t.y + t.height - t.radius, t.radius, 0 * degrees, 90 * degrees)
    cairo_arc (cr, t.x + t.radius, t.y + t.height - t.radius, t.radius, 90 * degrees, 180 * degrees)
    cairo_arc (cr, t.x + t.radius, t.y + t.radius, t.radius, 180 * degrees, 270 * degrees)

    cairo_close_path (cr)


        if #t.bg_colour == 1 then 
        cairo_set_source_rgba(cr,rgb_to_r_g_b2(t.bg_colour[1]))
    else
        local pat
        local pts=linear_orientation_bg(t)
        pat = cairo_pattern_create_linear (pts[1], pts[2], pts[3], pts[4])

        for i=1, #t.bg_colour do
            cairo_pattern_add_color_stop_rgba (pat, t.bg_colour[i][1], rgb_to_r_g_b2(t.bg_colour[i]))
        end

        cairo_set_source (cr, pat)
        cairo_fill (cr)
        cairo_pattern_destroy(pat)
    end
end[/HTML]

Multiple shadows or? Can you post some screenshot and *how to*?

---

### Post by olgmen on 2010-12-19
I apologize for the incomplete script laid out earlier.
I have no practice in writing in English, and so I am using an electronic translator.

[[IMG]http://storage6.static.itmages.ru/i/10/1219/s_1292768269_42c22ea3b0.png[/IMG]]("http://itmages.ru/image/view/93125/42c22ea3")



```
--[[ backgraund.lua &#1086;&#1090; olgmen 16.11.2010

&#1042;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090; &#1074; &#1086;&#1082;&#1085;&#1086; conky &#1092;&#1086;&#1085; &#1089; &#1075;&#1088;&#1072;&#1076;&#1080;&#1077;&#1085;&#1090;&#1085;&#1086;&#1081; &#1086;&#1082;&#1088;&#1072;&#1089;&#1082;&#1086;&#1081;
&#1044;&#1083;&#1103; &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090;&#1072; &#1087;&#1086;&#1084;&#1077;&#1089;&#1090;&#1080;&#1090;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1089;&#1090;&#1088;&#1086;&#1082;&#1080; &#1074; conkyrc &#1074;&#1099;&#1096;&#1077; &#1089;&#1083;&#1086;&#1074;&#1072; TEXT

Displays the window conky background with gradient color
To run the script put the following lines to the above words conkyrc 

lua_load /path/to/the/lua/script/backgraund.lua
lua_draw_hook_pre draw_content

]]
require 'cairo'

function conky_draw_content()


backgraund_settings={

{            -- default

--x = 160,        -- &#1082;&#1086;&#1086;&#1088;&#1076;&#1080;&#1085;&#1072;&#1090;&#1099; x, &#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102; = 0
            -- coordinates x, default = 0

--y = 10,        -- &#1082;&#1086;&#1086;&#1088;&#1076;&#1080;&#1085;&#1072;&#1090;&#1099; y, &#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102; = 0
            -- coordinates x, default = 0

--height = 145,        -- &#1074;&#1099;&#1089;&#1086;&#1090;&#1072;, &#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102; &#1074;&#1099;&#1089;&#1086;&#1090;&#1072; &#1086;&#1082;&#1085;&#1072;
            -- height, the default window height

--width = 150,        -- &#1096;&#1080;&#1088;&#1080;&#1085;&#1072;, &#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102; &#1096;&#1080;&#1088;&#1080;&#1085;&#1072; &#1086;&#1082;&#1085;&#1072;
            -- width, the default width of the window

--orientation = "ne",    -- &#1075;&#1088;&#1072;&#1076;&#1072;&#1094;&#1080;&#1103;, &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1085;&#1099; "nn", "ne", "ee", "se", "ss", "sw", "ww", "nw"
            --    &#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102; "ww"
            -- Graduations, available "nn", "ne", "ee", "se", "ss", "sw", "ww", "nw"
            -- default "ww"

--bg_colour = {{0, 0x31489c, 0.5},{0.5, 0x9c5930, 0.75},{1, 0x889c30, 0.3}},
},

{            -- top left

x = 10,
y = 10,
height = 145,
width = 140,
orientation = "ne",
bg_colour = {{0, 0x31489c, 0.5},{0.5, 0x9c5930, 0.75},{1, 0x889c30, 0.3}},

},

{            -- top right

x = 160,
y = 10,
height = 145,
width = 140,
orientation = "ww",
bg_colour = {{0, 0x00ffff, 0.1},{0.5, 0x00FFFF, 0.5},{1, 0x00FFFF, 0.1}},

},

{            -- bottom left

x = 10,
y = 170,
height = 145,
width = 140,
orientation = "nn",

},

}

    if conky_window==nil then return end

    local cs=cairo_xlib_surface_create(conky_window.display,
        conky_window.drawable, 
        conky_window.visual, conky_window.width, conky_window.height)
    cr=cairo_create(cs)



    for i,v in pairs(backgraund_settings) do
        display_background(v)
    end


cairo_destroy(cr)

end
-- ---------------------------------------
function display_background(t)

    if t.x            == nil then t.x = 0 end
    if t.y            == nil then t.y = 0 end
    if t.width        == nil then t.width = conky_window.width end
    if t.height        == nil then t.height = conky_window.height end
    if t.radius        == nil then t.radius = (t.width+t.height)/2*0.04 end
    if t.orientation    == nil then t.orientation = "ww" end

    if t.bg_colour == nil then
        t.bg_colour = {{0, 0xffffff, 0.5},{1, 0x000000, 0.5}}
    end

    local degrees = math.pi / 180.0

    cairo_new_sub_path (cr)

    cairo_arc (cr, t.x + t.width - t.radius, t.y + t.radius, t.radius, -90 * degrees, 0 * degrees)
    cairo_arc (cr, t.x + t.width - t.radius, t.y + t.height - t.radius, t.radius, 0 * degrees, 90 * degrees)
    cairo_arc (cr, t.x + t.radius, t.y + t.height - t.radius, t.radius, 90 * degrees, 180 * degrees)
    cairo_arc (cr, t.x + t.radius, t.y + t.radius, t.radius, 180 * degrees, 270 * degrees)

    cairo_close_path (cr)

-- &#1083;&#1080;&#1085;&#1077;&#1081;&#1085;&#1072;&#1103; &#1075;&#1088;&#1072;&#1076;&#1072;&#1094;&#1080;&#1103;

        if #t.bg_colour == 1 then 
        cairo_set_source_rgba(cr,rgb_to_r_g_b2(t.bg_colour[1]))
    else
        local pat
        local pts=linear_orientation_bg(t)
        pat = cairo_pattern_create_linear (pts[1], pts[2], pts[3], pts[4])

        for i=1, #t.bg_colour do
            cairo_pattern_add_color_stop_rgba (pat, t.bg_colour[i][1], rgb_to_r_g_b2(t.bg_colour[i]))
        end

        cairo_set_source (cr, pat)
        cairo_fill (cr)
        cairo_pattern_destroy(pat)
    end
end

-- ---------------------------------------
function rgb_to_r_g_b2(tcolour)
    colour, alpha = tcolour[2], tcolour[3]
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
-- ----------------------------------------

function linear_orientation_bg(t)

    if t.orientation    == "nn" then
        p = {t.x + t.width/2, t.y, t.x + t.width/2, t.y + t.height}
    elseif t.orientation    == "ne" then
        p = {t.x + t.width, t.y, t.x, t.y + t.height}
    elseif t.orientation    == "ee" then
        p = {t.x + t.width, t.y + t.height/2, t.x, t.y + t.height/2}
    elseif t.orientation    == "se" then
        p = {t.x +t.width, t.y + t.height, t.x, t.y}
    elseif t.orientation    == "ss" then
        p = {t.x + t.width/2, t.y + t.height, t.x + t.width/2, t.y}
    elseif t.orientation    == "sw" then
        p = {t.x, t.y + t.height, t.x + t.width, t.y}
    elseif t.orientation    == "ww" then
        p = {t.x, t.y + t.height/2, t.x + t.width, t.y + t.height/2}
    else
        p = {t.x, t.y, t.x + t.width, t.y + t.height}
    end

    return p
end
```

---

### Post by vickoxy on 2010-12-19
Thanks a lot :popcorn: this looks beautiful...

So, i made some modifications to suite my needs. Thanks a lot olgmen -this is really nice job and very easy to adapt even to total amateurs as me...
```
--[[ backgraund.lua &#1086;&#1090; olgmen 16.11.2010

&#1042;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090; &#1074; &#1086;&#1082;&#1085;&#1086; conky &#1092;&#1086;&#1085; &#1089; &#1075;&#1088;&#1072;&#1076;&#1080;&#1077;&#1085;&#1090;&#1085;&#1086;&#1081; &#1086;&#1082;&#1088;&#1072;&#1089;&#1082;&#1086;&#1081;
&#1044;&#1083;&#1103; &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090;&#1072; &#1087;&#1086;&#1084;&#1077;&#1089;&#1090;&#1080;&#1090;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1089;&#1090;&#1088;&#1086;&#1082;&#1080; &#1074; conkyrc &#1074;&#1099;&#1096;&#1077; &#1089;&#1083;&#1086;&#1074;&#1072; TEXT

Displays the window conky background with gradient color
To run the script put the following lines to the above words conkyrc 

lua_load /path/to/the/lua/script/backgraund.lua
lua_draw_hook_pre draw_content

]]
require 'cairo'

function conky_draw_content()


backgraund_settings={



{            -- top

x = 1,
y = 1,
height = 185,
width = 190,
orientation = "ne",
bg_colour = {{0, 0x000000, 0.3},{0.5, 0x000000, 0.3},{1, 0x000000, 0.3}},

},

{            -- middle

x = 1,
y = 192,
height = 206,
width = 190,
orientation = "ww",
bg_colour = {{0, 0x000000, 0.3},{0.5, 0x000000, 0.3},{1, 0x000000, 0.3}},

},

{            -- bottom

x = 1,
y = 404,
height = 111,
width = 190,
orientation = "nn",

},

}

    if conky_window==nil then return end

    local cs=cairo_xlib_surface_create(conky_window.display,
        conky_window.drawable, 
        conky_window.visual, conky_window.width, conky_window.height)
    cr=cairo_create(cs)



    for i,v in pairs(backgraund_settings) do
        display_background(v)
    end


cairo_destroy(cr)

end
-- ---------------------------------------
function display_background(t)

    if t.x            == nil then t.x = 0 end
    if t.y            == nil then t.y = 0 end
    if t.width        == nil then t.width = conky_window.width end
    if t.height        == nil then t.height = conky_window.height end
    if t.radius        == nil then t.radius = (t.width+t.height)/2*0.04 end
    if t.orientation    == nil then t.orientation = "ww" end

    if t.bg_colour == nil then
        t.bg_colour = {{0, 0x000000, 0.3},{1, 0x000000, 0.3}}
    end

    local degrees = math.pi / 180.0

    cairo_new_sub_path (cr)

    cairo_arc (cr, t.x + t.width - t.radius, t.y + t.radius, t.radius, -90 * degrees, 0 * degrees)
    cairo_arc (cr, t.x + t.width - t.radius, t.y + t.height - t.radius, t.radius, 0 * degrees, 90 * degrees)
    cairo_arc (cr, t.x + t.radius, t.y + t.height - t.radius, t.radius, 90 * degrees, 180 * degrees)
    cairo_arc (cr, t.x + t.radius, t.y + t.radius, t.radius, 180 * degrees, 270 * degrees)

    cairo_close_path (cr)

-- &#1083;&#1080;&#1085;&#1077;&#1081;&#1085;&#1072;&#1103; &#1075;&#1088;&#1072;&#1076;&#1072;&#1094;&#1080;&#1103;

        if #t.bg_colour == 1 then 
        cairo_set_source_rgba(cr,rgb_to_r_g_b2(t.bg_colour[1]))
    else
        local pat
        local pts=linear_orientation_bg(t)
        pat = cairo_pattern_create_linear (pts[1], pts[2], pts[3], pts[4])

        for i=1, #t.bg_colour do
            cairo_pattern_add_color_stop_rgba (pat, t.bg_colour[i][1], rgb_to_r_g_b2(t.bg_colour[i]))
        end

        cairo_set_source (cr, pat)
        cairo_fill (cr)
        cairo_pattern_destroy(pat)
    end
end

-- ---------------------------------------
function rgb_to_r_g_b2(tcolour)
    colour, alpha = tcolour[2], tcolour[3]
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
-- ----------------------------------------

function linear_orientation_bg(t)

    if t.orientation    == "nn" then
        p = {t.x + t.width/2, t.y, t.x + t.width/2, t.y + t.height}
    elseif t.orientation    == "ne" then
        p = {t.x + t.width, t.y, t.x, t.y + t.height}
    elseif t.orientation    == "ee" then
        p = {t.x + t.width, t.y + t.height/2, t.x, t.y + t.height/2}
    elseif t.orientation    == "se" then
        p = {t.x +t.width, t.y + t.height, t.x, t.y}
    elseif t.orientation    == "ss" then
        p = {t.x + t.width/2, t.y + t.height, t.x + t.width/2, t.y}
    elseif t.orientation    == "sw" then
        p = {t.x, t.y + t.height, t.x + t.width, t.y}
    elseif t.orientation    == "ww" then
        p = {t.x, t.y + t.height/2, t.x + t.width, t.y + t.height/2}
    else
        p = {t.x, t.y, t.x + t.width, t.y + t.height}
    end

    return p
end
```

---

### Post by wlourf on 2010-12-19
Hi olgmen, I recognize the "orientation" parameter I usually use when I don't know in advance the size of a shape! 

Here is my contribution to the boxes : I don't use the orientation parameter but the user can set the gradient with theses parameters:
a linear gradient is defined by two points 
```
linear_gradient = {x1,y1,x2,y2},
```or
a radial gradient is defined by two circles (x and y center and radius)
```
radial_gradient = {x1,y1,r1,x2,y2,r2 },
```I added another way to draw corners :
[IMG]http://uppix.com/f-corners4d0e33340007db42.png[/IMG]
The top one is the default corner, the bottom one is draw with the parameter
```
mode="circle",
```I also added a border parameter (default=0) but if border>0 then only the border is drawn.

Tweaking with the 9 parameters give the image attached, with rectangles, circles or amazing and useless shapes!:P

**Note : The script has been updated later in this topic : [http://ubuntuforums.org/showpost.php?p=10403895&postcount=281](http://ubuntuforums.org/showpost.php?p=10403895&postcount=281)**

---

### Post by Creamy Goodness on 2010-12-19
hi wlourf,
i found your scripts on deviantart and your blog a few days ago. i really like the designs and patterns i can make with them, although it takes me a long time to come up with anything that looks good.
I am running conky on a mobile phone (nokia n900) and the memory and cpu is quite limited. I noticed conky was eating about 100mb of ram overnight so I spent a considerable amount of time trying to figure out enough cairo and lua to stop any memory leaks. I am not sure how well the garbage collection works in lua with global vars, in the end the last memory leaks I found were from some missing cairo_pattern_destroys. But there might have been more leaks from failing to take ownership of matrixes and font extents, and the other normal lua variables getting lost. I am attaching fixed versions of the scripts I am using from you, and also a scripts I found that might help in the future:
strict.lua - i found this file online somewhere, it's supposed to prevent you from accidentally making global vars, i changed it to just print a warning though.

p.s.
i found this conky variable "to_bytes" useful with your scripts because it will convert a string value like 123M or 123mb (mib?) or whatever back into a real number by multiplying it by 1024 a few times, but it seemed to be broken because it only accepts integers and of course conky returns decimals all the time (12.3G). Luckily it was[ easy to fix]("https://garage.maemo.org/plugins/ggit/browse.php/?p=monky;a=commitdiff;h=174c256c81a027a2ea406f5f37dc036fac0a524b;hp=d75e2db5ed3fc788fb8514121f67316ac3e5f29f"), but it's not going to help the rest of you unless you recompile or report the bug.

screenshot: [IMG]http://www.appcheck.net/storage/Screenshot-20101219-211628.jpg[/IMG]

---

### Post by maman on 2010-12-22
Hello, I'm happy to join the communauty :)  Well, I've got a problem with my conky and I can't find any issu. 

I'd like to have rings for:

[LIST]
[*]cpu0 perc
[*]cpu1 perc
[*]ram perc
[*]space used by "/"
[*]space used by "/home"
[/LIST]
All is OK, except for "/home". Here is a screenshot and the lua 
[IMG]http://pix.toile-libre.org/upload/original/1293039367.jpg[/IMG]
```
--[[
--Ring Meters by londonali1010 (2009)
-- 
-- This script draws percentage meters as rings. It is fully customisable; all options are described in the script.
--  
--  IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num > 5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num > 3; conversely if you update Conky every 0.5s, you should use update_num > 10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.
--   
--   To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
--       lua_load ~/scripts/rings-v1.2.1.lua
--
--       lua_draw_hook_pre ring_stats
 
Changelog:
+ v1.2.1 -- Fixed minor bug that caused script to crash if conky_parse() returns a nil value (20.10.2009)
+ v1.2 -- Added option for the ending angle of the rings (07.10.2009)
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]
 
settings_table = {
    {
        name='cpu',
        arg='cpu0',
        max=100,
        bg_colour=0xFFFFFF,
        bg_alpha=0.2,
        fg_colour=0xFFFFFF,
        fg_alpha=1,
        x=60, y=80,
        radius=40,
        thickness=5,
        start_angle=0,
        end_angle=180
    },
    {
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=0xFFFFFF,
        bg_alpha=0.2,
        fg_colour=0xFFFFFF,
        fg_alpha=1,
        x=59, y=160,
        radius=40,
        thickness=5,
        start_angle=180,
        end_angle=360
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0xFFFFFF,
        bg_alpha=0.2,
        fg_colour=0xFFFFFF,
        fg_alpha=1,
        x=60, y=240,
        radius=40,
        thickness=5,
        start_angle=0,
        end_angle=180
    },
    {
    name='fs_used_perc',
    arg='/',
    max=100,
    bg_colour=0xFFFFFF,
    bg_alpha=0.2,
    fg_colour=0xFFFFFF,
    fg_alpha=1,
        x=59, y=320,
        radius=40,
        thickness=5,
    start_angle=180,
        end_angle=360
    },
    {
    name='fs_used_perc',        
    arg='/home',
        max=100,
        bg_colour=0xFFFFFF,
        bg_alpha=0.2,
        fg_alpha=0xFFFFFF,
        fg_alpha=1,
        x=60, y=400,
        radius=40,
        thickness=5,
        start_angle=0,
        end_angle=180
    },
} 

require 'cairo'
 
function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
 
function draw_ring(cr,t,pt)
    local w,h=conky_window.width,conky_window.height
 
    local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
 
    local angle_0=sa*(2*math.pi/360)-math.pi/2
    local angle_f=ea*(2*math.pi/360)-math.pi/2
    local t_arc=t*(angle_f-angle_0)
 
    -- Draw background ring
 
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
 
    -- Draw indicator ring
 
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
end
 
function conky_ring_stats()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
 
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
 
        value=tonumber(str)
        if value == nil then value = 0 end
        pct=value/pt['max']
 
        draw_ring(cr,pct,pt)
    end
 
    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
 
    local cr=cairo_create(cs)    
 
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
 
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
    end
end

```I have also this message : "Conky: llua_do_call: function conky_ring_stats execution failed: scripts/slalom.lua:96: attempt to perform arithmetic on local 'colour' (a nil value)"
The ligne # 96 is : "return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha"

Can somebody help me to fix this ? Thank you.

---

### Post by jo-shva on 2010-12-26
I finished the first part of my conky using graph and ring lua scripts to draw the background images and shadows.  And was able to use 4 lua scripts in my conky.  
Here is what i have so far....the first is on my changing earth desktop the second is a clearer image on colored wallpaer.
Should i post my configs/luas here or not??
If anyones interested let me know and ill post them.
Thanks especially to Wlourf!!!

---

### Post by miegiel on 2010-12-26
> **jo-shva said:**
> I finished the first part of my conky using graph and ring lua scripts to draw the background images and shadows.  And was able to use 4 lua scripts in my conky.  
Here is what i have so far....the first is on my changing earth desktop the second is a clearer image on colored wallpaer.

Nice, I like the symmetry. I don't know if it's possible to flip the graphs of download and core 2, so that they point down. Just a thought. :D

> Should i post my configs/luas here or not??
If anyones interested let me know and ill post them.
Thanks especially to Wlourf!!!

I say: "Always post scripts, you never know who you'll inspire!"

---

### Post by wlourf on 2010-12-26
> **Creamy Goodness said:**
> hi wlourf,
i found your scripts on deviantart and your blog a few days ago. i really like the designs and patterns i can make with them, although it takes me a long time to come up with anything that looks good.
I am running conky on a mobile phone (nokia n900) and the memory and cpu is quite limited. I noticed conky was eating about 100mb of ram overnight so I spent a considerable amount of time trying to figure out enough cairo and lua to stop any memory leaks. I am not sure how well the garbage collection works in lua with global vars, in the end the last memory leaks I found were from some missing cairo_pattern_destroys. But there might have been more leaks from failing to take ownership of matrixes and font extents, and the other normal lua variables getting lost. I am attaching fixed versions of the scripts I am using from you, and also a scripts I found that might help in the future:
strict.lua - i found this file online somewhere, it's supposed to prevent you from accidentally making global vars, i changed it to just print a warning though.

p.s.
i found this conky variable "to_bytes" useful with your scripts because it will convert a string value like 123M or 123mb (mib?) or whatever back into a real number by multiplying it by 1024 a few times, but it seemed to be broken because it only accepts integers and of course conky returns decimals all the time (12.3G). Luckily it was[ easy to fix]("https://garage.maemo.org/plugins/ggit/browse.php/?p=monky;a=commitdiff;h=174c256c81a027a2ea406f5f37dc036fac0a524b;hp=d75e2db5ed3fc788fb8514121f67316ac3e5f29f"), but it's not going to help the rest of you unless you recompile or report the bug.

screenshot: [IMG]http://www.appcheck.net/storage/Screenshot-20101219-211628.jpg[/IMG]

Hi Creamy Goodness,

Thanks for your feedback and your improvments to the scripts.
I started to look to some scripts you have modified, I like the DrawMe flag and the _to_byte variables and I will add them in futures updates.

I've seen somewhere in a script, that you use :
```
    name="fs_used",
    arg="/",
    max=conky_parse("${to_bytes ${fs_size /}}"),
```but you can find variables with named with _perc , they give you percentages, like fs_used_perc, memperc... so you can use this table :
```
            name="fs_used_perc",
            arg="/",
            max=100,
```For the memory leaks (well I have to improve myself, I agree! the N900 has really 256 MB of memory? ) :
I didn't know "tolua.takeownership()", what does it do exactly ?
I agree : we have to destroy patterns, so I missed somes !

But are you sure that global variables create memory leaks ? When the conky runs, a global variable is overwritten each time the script is called, so memory usage should not increase.
And if we use only local variables, I'm not sure to set the variable to "nil" at the end of the script is necessary.

Anyway, local variables are a good practice and I will update the scripts with them and with your ideas soon.

So now, two questions : what is the best tool to see if the memory used by conky is increasing ( top | grep conky ; pmap ?)
I would like to put all my little scripts at the same place so it become more easy to find them and more easy to modify them for anyone who want to do it ! Any idea ? I thought of ubuntu PPA but I don't use ubuntu actually !

Thanks again

---

### Post by wlourf on 2010-12-26
double post , sorry :
@maman, welcome!
in your table settings, change :
```
    {
    name='fs_used_perc',        
    arg='/home',
        max=100,
        bg_colour=0xFFFFFF,
        bg_alpha=0.2,
       [COLOR=Red] fg_alpha=0xFFFFFF,[/COLOR]
        fg_alpha=1,
        x=60, y=400,
        radius=40,
        thickness=5,
        start_angle=0,
        end_angle=180
    },
```to
```
    {
    name='fs_used_perc',        
    arg='/home',
        max=100,
        bg_colour=0xFFFFFF,
        bg_alpha=0.2,
        [COLOR=Red]fg_colour=0xFFFFFF,[/COLOR]
        fg_alpha=1,
        x=60, y=400,
        radius=40,
        thickness=5,
        start_angle=0,
        end_angle=180
    },
```@jo-shva
I agree with miegiel, scripts are always welcome, here or in the conky mega-thread! I like the top bar (the one who contains uptime) for the colors and font used, is it an image or a box drawn with Lua ?

---

### Post by jo-shva on 2010-12-27
Thanks.  I will post them, i am cleaning up the scripts first.  The entire image top and bottom bars and shadows...everything is drawn in Lua, using your scripts Wlourf.  I'll post them tomorrow.  Miegiel, I was able to flip those bars per your suggestion.  Thanks that was a great idea!!!

I have noticed memory leaks.  If i leave my laptop on overnight conky will be using 35%+ of my 2.7Gigs of Memory.  X will begin consuming large amounts of cpu after 5 or more hours uptime 33-68% cpu!!! If i 'killall conky' and restart conky everything goes back to normal useage and the whole cycle begins again....Any Ideas as to how to address this issue?
--Thanks Jo-shva

---

### Post by wlourf on 2010-12-28
Hi,
I guess some of your conkys don't need a fast refresh, for the background for example. Maybe you can split theses conkys in two parts.
For the memory leaks, I am ashamed to have not seen them before. I'm working on it, with the ideas of Creamy G. and I will post corrected versions this week.

For Xorg, somme people use cron to kill and restart all conky occasionaly : [see here]("http://ubuntuforums.org/showpost.php?p=10272775&postcount=15469").

hth

---

### Post by jo-shva on 2010-12-28
I'll take a look at the cron fix.  And, I'll be looking forward to the fixes for the memory leaks.  In the mean time here are my configs.
conkyrc:```
# -- Conky settings meters-- #
background no
update_interval 1.0

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes
format_human_readable yes

double_buffer yes
no_buffers yes

text_buffer_size 4048
imlib_cache_size 0
imlib_cache_flush_interval 0

# -- Window specifications -- #

own_window yes
own_window_type normal
own_window_transparent yes
own_window_argb_visual yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_title graph widgets

border_inner_margin 0
border_outer_margin 0

minimum_size 1000 160

alignment bm
gap_y -24
gap_x -54

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# -- Text settings -- #
use_xft yes
xftfont Inconsolata-g:size=6
xftalpha 0.8

uppercase no

# +++++ Colors +++++
default_shade_color ffffff
default_color FFFFFF

# -- Lua load -- #
lua_load ~/.conky/conkyparts/graph.lua
lua_load ~/.conky/conkyparts/ring.lua ~/.conky/conkyparts/bargraph1.lua ~/.conky/conkyparts/text.lua
lua_draw_hook_pre main_graph
lua_draw_hook_post main_rings

# -- Begin Conky Text -- #

TEXT
# -- Top Bar -- #
${font Droid Sans Mono:Bold:size=7}
${color #5a5a5a}${goto 825}${voffset 39}GPU${goto 725}NET${goto 146}CPU${goto 51}MEM
${color #4a4a4a}${goto 826}${voffset -11}GPU${goto 726}NET${goto 145}CPU${goto 50}MEM
${color #eeeeee}${goto 825}${voffset -12}GPU${goto 725}NET${goto 146}CPU${goto 51}MEM
${color #5a5a5a}${alignc 54}${voffset -13}${kernel}
${color #4a4a4a}${alignc 55}${voffset -11}${kernel}
${color #eeeeee}${alignc 54}${voffset -12}${kernel}
${font Droid Sans Mono:Bold:size=5}${shadecolor #cccccc}
${color #aaaaaa}${alignc 54}${voffset -12}Uptime: ${uptime}
${color #1a1a1a}${alignc 54}${voffset -10}Uptime: ${uptime}
${color #aaaaaa}${goto 353}PROC${goto 445}PID${goto 481}CPU%${goto 521}MEM%
${color #1a1a1a}${goto 353}${voffset -10}PROC${goto 445}PID${goto 481}CPU%${goto 521}MEM%
${color #aaaaaa}${goto 213}${voffset -22}${execi 300 cat /proc/cpuinfo | grep 'model name' | head -n1 | sed -e 's/model name.*: //' | cut -c 1-10}${goto 623}${addr wlan0}${goto 793}${execi 300 lspci | grep VGA | tail -c+36 | head -n1 | cut -c 1-6}
${color #2a2a2a}${goto 213}${voffset -10}${execi 300 cat /proc/cpuinfo | grep 'model name' | head -n1 | sed -e 's/model name.*: //' | cut -c 1-10}${goto 623}${addr wlan0}${goto 793}${execi 300 lspci | grep VGA | tail -c+36 | head -n1 | cut -c 1-6}
${color #aaaaaa}${goto 213}${execi 300 cat /proc/cpuinfo | grep 'model name' | head -n1 | sed -e 's/model name.*: //' | cut -c 12-26}${goto 600}.::${execi 120 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'}::.${goto 758}${execi 300 lspci | grep VGA | tail -c+36 | head -n1 | cut -c 24-41}
${color #2a2a2a}${goto 213}${voffset -10}${execi 300 cat /proc/cpuinfo | grep 'model name' | head -n1 | sed -e 's/model name.*: //' | cut -c 12-26}${goto 600}.::${execi 120 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'}::.${goto 758}${execi 300 lspci | grep VGA | tail -c+36 | head -n1 | cut -c 24-41}
${color #aaaaaa}${goto 76}${voffset -12}${memmax}::.
${color #2a2a2a}${goto 76}${voffset -10}${memmax}::.
# -- End Top Bar -- #
${font}
# -- MEM -- #
${color #aaaaaa}${goto 64}${voffset 19}$mem${alignr 871}$memperc%
${color #000000}${goto 64}${voffset -11}$mem${alignr 871}$memperc%
${color #aaaaaa}${goto 64}${voffset 6}Swap:$swap${alignr 871}$swapperc%
${color #000000}${goto 64}${voffset -11}Swap:$swap${alignr 871}$swapperc%
# -- CPU -- #
${color #aaaaaa}${alignc 345}${voffset -39}${hwmon temp 1}°
${color #000000}${alignc 345}${voffset -11}${hwmon temp 1}°
${goto 170}${freq_g cpu1}Ghz${alignr 676}${cpu cpu1%}%
${goto 170}${voffset 12}${freq_g cpu2}Ghz${alignr 676}${cpu cpu2%}%
# -- PROC --#
${goto 353}${voffset -39}${top name 1}     ${top pid 1}    ${top cpu 1}    ${top mem 1}
${goto 353}${color #1a1a1a}${top name 2}     ${top pid 2}    ${top cpu 2}    ${top mem 2}
${goto 353}${color #000000}${top name 3}     ${top pid 3}    ${top cpu 3}    ${top mem 3}
${goto 353}${color #1a1a1a}${top name 4}     ${top pid 4}    ${top cpu 4}    ${top mem 4}
${color #000000}
# -- NET -- #
${font VariShapes Solid:size=5}
${color #2a2a2a}${goto 561}${voffset -54}q ${font}${color #000000}${upspeedf wlan0}ks${alignr 266}M:${execi 300 python2 ~/.conky/conkyparts/vnstat-conky-script.py -s}
${color #2a2a2a}${font VariShapes Solid:size=5}${goto 561}${voffset 10}Q ${font}${color #000000}${downspeedf wlan0}ks${alignr 266}M:${execi 300 python2 ~/.conky/conkyparts/vnstat-conky-script.py -r}
${alignr 266}${voffset -39}D:${execi 300 python2 ~/.conky/conkyparts/vnstatDAILY-conky-script.py -s}
${alignr 266}${voffset 12}D:${execi 300 python2 ~/.conky/conkyparts/vnstatDAILY-conky-script.py -r}
# -- GPU -- #
${color #aaaaaa}${alignc -257}${voffset -35}${nvidia temp}°
${color #000000}${alignc -257}${voffset -11}${nvidia temp}°
${color #aaaaaa}${goto 816}${voffset -3}${nvidia gpufreq}MHz
${color #000000}${goto 816}${voffset -11}${nvidia gpufreq}MHz
${color #aaaaaa}${goto 774}${voffset 7}Driver:${alignr 162}${execi 300 cat /proc/driver/nvidia/version | awk '/NVIDIA/ {print $8}'}
${color #000000}${goto 774}${voffset -11}Driver:${alignr 162}${execi 300 cat /proc/driver/nvidia/version | awk '/NVIDIA/ {print $8}'}
```
graph.lua:
```
--[[ GRAPH widget v1.0 by wlourf (31.10.2010)
	this widget draws some graphs with some effects 
	http://u-scripts.blogspot.com/2010/10/graph-widget.html
	
To call the script in a conky, use, before TEXT
	lua_load /path/to/the/script/graph.lua
	lua_draw_hook_pre main_graph
and add one line (blank or not) after TEXT


Parameters are :
3 parameters are mandatory
name		- the name of the conky variable to display,
			  for example for {$cpu cpu0}, just write name="cpu"
arg			- the argument of the above variable,
			  for example for {$cpu cpu1}, just write arg="cpu1"
		  	  arg can be a numerical value if name=""
max			- the maximum value the above variable can reach,
			  for example for {$cpu cpu1}, just write max=100 or less or more
	
Optional parameters:
x,y 		- coordinates of the bottom-left corner of the graph,
              relative to the top-left corner of the conky window 
			  default =  bottom-left corner of the conky window
width       - width of the graph, default = 100 pixels
height      - height of the graph, default = 20 pixels
nb_values   - number of values to display in the graph, default=width 
              i.e. 1 pixel for 1 value
autoscale   - if set to true, calculate the max valeu of the y axis and
              doesn't use the max parameter above, default=false
skew_x      - skew graph around x axis, défaut = 0
skew_y      - skew graph around y axis, défaut = 0
angle	    - angle of rotation of the graph in degress, default = 0
              i.e. a horizontal graph)
inverse     - if set to true, graph are draw from right to left, default=false
background  - if set to false, background is not drawn, default=true
foreground  - if set to false, foreground is not drawn, default=true
              foreground = plain graph
bg_bd_size  - size of the border of the background, default=0=no border
fg_bd_size  - size of the border of the foreground, default=0=no border


Colours tables below are defined into braces :
{position in the gradient (0 to 1), colour in hexadecimal, alpha (0 to 1)}
example for a single colour table : 
{{0,0xFFAA00,1}} position parameter doesn't matter
example for a two-colours table : 
{{0,0xFFAA00,1},{1,0x00AA00,1}} or {{0.5,0xFFAA00,1},{1,0x00AA00,1}}
example for a three-colours table : 
{{0,0xFFAA00,1},{0.5,0xFF0000,1},{1,0x00AA00,1}}

bg_colour	- colour table for background,
			  default = {{0,0x000000,.5},{1,0xFFFFFF,.5}}
fg_colour	- colour table for foreground,
			  default = {{0,0x00FFFF,1},{1,0x0000FF,1}}
bg_bd_colour- colour table for background border,
			  default = {{1,0xFFFFFF,1}}			  
fg_bd_colour- colour table for foreground border,
			  default = {{1,0xFFFF00,1}}			  

bg_orientation, bg_bd_orientation, fg_orientation, fg_bd_orientation,
        	- "orientation" defines the starting point of the gradient,
        	  default="nn"
			  there are 8 available starting points : 
			  "nw","nn","ne","ee","se","ss","sw","ww"
			  (n for north, w for west ...)
			  theses 8 points are the 4 corners + the 4 middles of graph
			  so a gradient "nn" will go from "nn" to "ss"
			  a gradient "nw" will go from "nw" to "se"


v1.0 (31 Oct. 2010) original release

--      This program is free software; you can redistribute it and/or modify
--      it under the terms of the GNU General Public License as published by
--      the Free Software Foundation version 3 (GPLv3)
--     
--      This program is distributed in the hope that it will be useful,
--      but WITHOUT ANY WARRANTY; without even the implied warranty of
--      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
--      GNU General Public License for more details.
--     
--      You should have received a copy of the GNU General Public License
--      along with this program; if not, write to the Free Software
--      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
--      MA 02110-1301, USA.

]]

require 'cairo'

function set_settings()
     graph_settings={
--GLASS TOP----------------------------------------------------------
     --Top Glass Base and Outline
      {
	    name="time",
	    arg="%M",
	    max=60,
        y=81,
        x=46,
        width=802,
        height=30,
        foreground=false,
        bg_bd_size=0.5,
        bg_colour = { {0,0xffffff,0.5},{0.4,0xFFFFFF,0.1},{1,0xffffff,0}},
        bg_bd_colour = { {0,0xFFFFFF,1},{1,0xFFFFFF,0}},        
        bg_orientation="nn",
	    },	
   --Top Glass Inner Bevel
	    {
	    name="time",
	    arg="%M",
	    max=60,
        y=81,
        x=46,
        width=802,
        height=30,
        foreground=false,
        bg_colour = { {0,0xffffff,0},{0.5,0xFFFFFF,0.2},{1,0xffffff,0}},
        bg_orientation="ww",
	    },	
--END GLASS TOP---------------------------------------------
--
--SHADOWS---------------------------------------------------	    
	    --Top Shadow
	   {
	    name="time",
	    arg="%M",
	    max=60,
        y=51,
        x=45,
        width=804,
        height=11,
        foreground=false,
        bg_colour = { {0,0x000000,0},{0.5,0x000000,0.1},{1,0x000000,0.25}},
        bg_orientation="nn",
	    },	
	     --Top Shadow Right Side
	   {
	    name="time",
	    arg="%M",
	    max=60,
        y=82,
        x=849,
        width=11,
        height=31,
        foreground=false,
        bg_colour = { {0,0x000000,0.25},{0.5,0x000000,0.1},{1,0x000000,0}},
        bg_orientation="ww",
	    },	
	     --Top Shadow Left Side
	   {
	    name="time",
	    arg="%M",
	    max=60,
        y=82,
        x=34,
        width=11,
        height=31,
        foreground=false,
        bg_colour = { {0,0x000000,0},{0.5,0x000000,0.1},{1,0x000000,0.25}},
        bg_orientation="ww",
	    },	
	     --Bottom Shadow
	   {
	    name="time",
	    arg="%M",
	    max=60,
        y=141,
        x=45,
        width=804,
        height=11,
        foreground=false,
        bg_colour = { {0,0x000000,0.25},{0.5,0x000000,0.1},{1,0x000000,0}},
        bg_orientation="nn",
	    },	
	    --Left Side corner shadow
	    {
	    name="time",
	    arg="%M",
	    max=60,
        y=51,
        x=35.5,
        width=9.5,
        height=9.5,
        foreground=false,
        bg_colour = { {0,0x000000,0},{0.75,0x000000,0.1},{1,0x000000,0.25}},
        bg_orientation="nw",
	    },	
	     --Right Side corner shadow
	    {
	    name="time",
	    arg="%M",
	    max=60,
        y=51,
        x=849,
        width=9.5,
        height=9.5,
        foreground=false,
        bg_colour = { {0,0x000000,0.25},{0.25,0x000000,0.1},{1,0x000000,0}},
        bg_orientation="sw",
	    },	
--END SHADOWS-----------------------------------------------------------
--
--BASE BACKGROUND-------------------------------------------------------	    
     --Background###Set color value 000000 to 1a1a1a when using black background!
    {
	    name="time",
	    arg="%M",
	    max=60,
        y=130,
        x=45,
        width=804,
        height=48,
        foreground=false,
        bg_bd_size=2,
        bg_colour = { {0,0x000000,0.25},{0.5,0xffffff,0.4},{1,0x000000,0.25}},
        bg_bd_colour = { {0,0x000000,0},{0.5,0x000000,0.4},{1,0x000000,0}},        
        bg_orientation="ww",
        bg_bd_orientation="ww",
	    },	  
--END BASE BACKGROUND-------------------------------------------------
--
--BASE AVERAGE CPU FOREGROUND-----------------------------------------
	   {
	    name="cpu",
	    arg="cpu0",
	    max=100,
        y=106,
        x=45,
        autoscale=true,
        width=804,
        height=24,
        background=false,
        nb_values=201,       
        fg_colour = { {0,0xffffff,0},{0.5,0xffffff,0.4},{1,0xffffff,0}},
        fg_orientation="ww",
	    },	 
	    {
	    name="cpu",
	    arg="cpu0",
	    max=100,
        y=106,
        x=849,
        autoscale=true,
        width=804,
        height=24,
        angle=180,
        inverse=true,
        background=false,
        nb_values=201,        
        fg_colour = { {0,0xffffff,0},{0.5,0xffffff,0.4},{1,0xffffff,0}},
        fg_orientation="ww",
	    },	 
--END BASE AVERAGE CPU FOREGROUND----------------------------------
--
--INTERNAL GRAPHS-------------------------------------------------- 
     --CPU
{
	    name="cpu",
	    arg="cpu1",
	    max=100,
        y=104,
        x=167,
        autoscale=true,
        width=164,
        height=18,
        nb_values=164,
        bg_bd_size=0.5,
        bg_colour = { {0,0x000000,0},{0.5,0xFFFFFF,0.8},{1,0x000000,0}},
        bg_bd_colour = { {0,0x000000,0},{0.5,0x20262e,1},{1,0x000000,0}},        
        fg_colour = { {0,0x0066ff,0},{0.5,0x0066ff,1},{1,0x0066ff,0}},
        bg_orientation="ww",
        bg_bd_orientation="ww",
        fg_orientation="ww",
	    },	    
{
	    name="cpu",
	    arg="cpu2",
	    max=100,
        y=108,
        x=331,
        autoscale=true,
        width=164,
        height=18,
        nb_values=164,
        angle=180,
        inverse=true,
        bg_bd_size=0.5,
        bg_colour = { {0,0x000000,0},{0.5,0xFFFFFF,0.8},{1,0x000000,0}},
        bg_bd_colour = { {0,0x000000,0},{0.5,0x20262e,1},{1,0x000000,0}},        
        fg_colour = { {0,0x9900ff,0},{0.5,0x9900ff,1},{1,0x9900ff,0}},
        bg_orientation="ww",
        bg_bd_orientation="ww",
        fg_orientation="ww",
	    },	
	    
--DIVIDERS--------------------------------
	    ----proc left
	    {
	    name="time",
	    arg="%M",
	    max=60,
        y=126,
        x=335,
        width=6,
        height=40,
        foreground=false,
        bg_bd_size=0.5,
        bg_colour = { {0,0xffffff,0},{0.5,0x000000,0.4},{1,0xffffff,0}},
        bg_bd_colour = { {0,0x000000,0},{0.5,0x000000,0.5},{1,0x000000,0}},        
        bg_orientation="ww",
        bg_bd_orientation="ww",
	    },	
	    ----proc right
	      {
	    name="time",
	    arg="%M",
	    max=60,
        y=126,
        x=549,
        width=6,
        height=40,
        foreground=false,
        bg_bd_size=0.5,
        bg_colour = { {0,0xffffff,0},{0.5,0x000000,0.4},{1,0xffffff,0}},
        bg_bd_colour = { {0,0x000000,0},{0.5,0x000000,0.5},{1,0x000000,0}},        
        bg_orientation="ww",
        bg_bd_orientation="ww",
	    },	
	    ----net right
	    {
	    name="time",
	    arg="%M",
	    max=60,
        y=126,
        x=743,
        width=6,
        height=40,
        foreground=false,
        bg_bd_size=0.5,
        bg_colour = { {0,0xffffff,0},{0.5,0x000000,0.4},{1,0xffffff,0}},
        bg_bd_colour = { {0,0x000000,0},{0.5,0x000000,0.5},{1,0x000000,0}},        
        bg_orientation="ww",
        bg_bd_orientation="ww",
	    },	
	    ----cpu left
	    {
	    name="time",
	    arg="%M",
	    max=60,
        y=126,
        x=141,
        width=6,
        height=40,
        foreground=false,
        bg_bd_size=0.5,
        bg_colour = { {0,0xffffff,0},{0.5,0x000000,0.4},{1,0xffffff,0}},
        bg_bd_colour = { {0,0x000000,0},{0.5,0x000000,0.5},{1,0x000000,0}},        
        bg_orientation="ww",
        bg_bd_orientation="ww",
	    },	
--END DIVIDERS-----------------------------------------------
--
--ROWS/COLUMNS------------------------------------------------	    
	    --stripes proc
	    {
	    name="time",
	    arg="%M",
	    max=60,
        y=126,
        x=345,
        width=200,
        height=40,
        foreground=false,
        bg_bd_size=1,
        bg_colour = { {0,0x000000,0.1},{0.125,0xffffff,0},{0.25,0x000000,0.1},{0.375,0xffffff,0},{0.5,0x000000,0.1},{0.625,0xffffff,0},{0.75,0x000000,0.1},{0.875,0xffffff,0},{1,0x000000,0.1}},
        bg_bd_colour = { {0,0x000000,0.1},{0.5,0x000000,0.1},{1,0x000000,0.1}},        
        bg_orientation="nn",
	    },	
	    ---stripes mem
	    {
	    name="time",
	    arg="%M",
	    max=60,
        y=126,
        x=60,
        width=76,
        height=32,
        foreground=false,
        bg_bd_size=1,
        bg_colour = { {0,0x000000,0.1},{0.1,0xffffff,0},{0.2,0xffffff,0.1},{0.25,0xffffff,0.15},{0.3,0xffffff,0.1},{0.4,0xffffff,0},{0.5,0x000000,0.1},{0.6,0xffffff,0},{0.7,0xffffff,0.1},{0.75,0xffffff,0.15},{0.8,0xffffff,0.1},{0.9,0xffffff,0},{1,0x000000,0.1}},
        bg_bd_colour = { {0,0x000000,0.1},{0.5,0x000000,0.1},{1,0x000000,0.1}},        
        bg_orientation="nn",
	    },	
	    
	    ---stripes gpu
	    {
	    name="time",
	    arg="%M",
	    max=60,
        y=118,
        x=769,
        width=76,
        height=32,
        foreground=false,
        bg_bd_size=1,
        bg_colour = { {0,0x000000,0.1},{0.1,0xffffff,0},{0.2,0xffffff,0.1},{0.25,0xffffff,0.15},{0.3,0xffffff,0.1},{0.4,0xffffff,0},{0.5,0x000000,0.1},{0.6,0xffffff,0},{0.7,0xffffff,0.1},{0.75,0xffffff,0.15},{0.8,0xffffff,0.1},{0.9,0xffffff,0},{1,0x000000,0.1}},
        bg_bd_colour = { {0,0x000000,0.1},{0.5,0x000000,0.1},{1,0x000000,0.1}},
        bg_orientation="nn",
	    },	
--END ROWS/COLUMNS------------------------------------------------

	    --NET
	    {
	    name="upspeedf",
	    arg="wlan0",
	    max=100,
        y=104,
        x=559,
        autoscale=true,
        width=180,
        height=18,
        nb_values=180,
        bg_bd_size=1,
        bg_colour = { {0,0x000000,0},{0.5,0xFFFFFF,0.8},{1,0x000000,0}},
        bg_bd_colour = { {0,0x000000,0},{0.5,0x000000,1},{1,0x000000,0}},        
        fg_colour = { {0,0xe5ff00,0},{0.5,0xe5ff00,1},{1,0xe5ff00,0}},
        bg_orientation="ww",
        bg_bd_orientation="ww",
        fg_orientation="ww",
	    },	    	    
{
	    name="downspeedf",
	    arg="wlan0",
	    max=100,
        y=108,
        x=739,
        autoscale=true,
        width=180,
        height=18,
        angle=180,
        inverse=true,
        nb_values=180,
        bg_bd_size=1,
        bg_colour = { {0,0x000000,0},{0.5,0xFFFFFF,0.8},{1,0x000000,0}},
        bg_bd_colour = { {0,0x000000,0},{0.5,0x000000,1},{1,0x000000,0}},        
        fg_colour = { {0,0x00ff19,0},{0.5,0x00ff19,1},{1,0x00ff19,0}},
        bg_orientation="ww",
        bg_bd_orientation="ww",
        fg_orientation="ww",
	    },	  
--END INTERNAL GRAPHS--------------------------------------------	
       }
end


function check_settings(t)
    --tables are check only when conky start
	if t.name==nil and t.arg==nil then 
		print ("No input values ... use parameters 'name'" .. 
			" with 'arg' or only parameter 'arg' ") 
		return 1
	end

	if t.max==nil then
		print ("No maximum value defined, use 'max'")
		print ("for name=" .. t.name .. " with arg=" .. t.arg)
		return 1
	end
	if t.name==nil then t.name="" end
	if t.arg==nil then t.arg="" end
	return 0
end

function conky_main_graph()

    if conky_window == nil then return end
	    
    local w=conky_window.width
    local h=conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, 
            conky_window.drawable, conky_window.visual, w, h)
    cr=cairo_create(cs)

    updates=tonumber(conky_parse('${updates}'))
    --start drawing after "updates_gap" updates
    --prevent segmentation error for cpu
    updates_gap=5
    if updates==1 then    
        set_settings()
	    
	    flagOK=0
		for i in pairs(graph_settings) do
			if graph_settings[i].width==nil then graph_settings[i].width=100 end
        	if graph_settings[i].nb_values==nil then  
        	    graph_settings[i].nb_values= graph_settings[i].width
        	end
			--create an empty table to store values
			graph_settings[i]["values"]={}
			--beginning point
			graph_settings[i].beg = graph_settings[i].nb_values
			--graph_settings[i].beg = 0
			for j =1, graph_settings[i].nb_values do
			    graph_settings[i].values[j]=0
			end
		    graph_settings[i].flag_init=true
		    flagOK=flagOK + check_settings(graph_settings[i])

		end
    end

    if flagOK>0 then 
        --abort script if error in one of the tables
        print ("ERROR : Check the graph_setting table")
        return
    end

    --drawing process
    if updates > updates_gap then
		for i in pairs(graph_settings) do
			local nb_values=graph_settings[i].nb_values
			graph_settings[i].automax=0
			for j =1, nb_values do
				if graph_settings[i].values[j+1]==nil then 
				    graph_settings[i].values[j+1]=0 
				end
				
				graph_settings[i].values[j]=graph_settings[i].values[j+1]
				if j==nb_values then
					--store value
					if graph_settings[i].name=="" then
					    value=graph_settings[i].arg
					else
    					value=tonumber(conky_parse('${' .. 
    					    graph_settings[i].name .. " " ..
    					    graph_settings[i].arg ..'}'))
    			    end
					graph_settings[i].values[nb_values]=value
				end
				graph_settings[i].automax=math.max(graph_settings[i].automax,
				                                   graph_settings[i].values[j])
			end
            
			draw_graph(graph_settings[i])
		end
    end

    cairo_destroy(cr)
    cairo_surface_destroy(cs)

end


function draw_graph(t)
    --drawing function

    local function rgb_to_r_g_b(colour)
        return ((colour[2] / 0x10000) % 0x100) / 255., ((colour[2] / 0x100) % 0x100) / 255., (colour[2] % 0x100) / 255., colour[3]
    end
 
	local function linear_orientation(o,w,h)
	    --set gradient for bg and bg border
		if o=="nn" then
			p={w/2,h,w/2,0}
		elseif o=="ne" then
			p={w,h,0,0}
		elseif o=="ww" then
			p={0,h/2,w,h/2}
		elseif o=="se" then
			p={w,0,0,h}
		elseif o=="ss" then
			p={w/2,0,w/2,h}
		elseif o=="ee" then
			p={w,h/2,0,h/2}		
		elseif o=="sw" then
			p={0,0,w,h}
		elseif o=="nw" then
			p={0,h,w,0}
		end
		return p
	end

	local function linear_orientation_inv(o,w,h)
	    --set gradient for fg and fg border
		if o=="ss" then
			p={w/2,h,w/2,0}
		elseif o=="sw" then
			p={w,h,0,0}
		elseif o=="ee" then
			p={0,h/2,w,h/2}
		elseif o=="nw" then
			p={w,0,0,h}
		elseif o=="nn" then
			p={w/2,0,w/2,h}
		elseif o=="ww" then
			p={w,h/2,0,h/2}		
		elseif o=="ne" then
			p={0,0,w,h}
		elseif o=="se" then
			p={0,h,w,0}
		end
		return p
	end
		
	--set default values
	if t.height==nil	then t.height=20 end
	--checked in previous part : width and nb_values
		
	if t.background==nil    then t.background=true end
	if t.bg_bd_size==nil	then t.bg_bd_size=0 end
	if t.x==nil 		    then t.x=t.bg_bd_size end
	if t.y==nil 		    then t.y=conky_window.height -t.bg_bd_size end
	if t.bg_colour==nil 	then t.bg_colour={{0,0x000000,.5},{1,0xFFFFFF,.5}} end
	if t.bg_bd_colour==nil 	then t.bg_bd_colour={{1,0xFFFFFF,1}} end
	
	if t.foreground==nil    then t.foreground=true end
	if t.fg_colour==nil 	then t.fg_colour={{0,0x00FFFF,1},{1,0x0000FF,1}} end
	
	if t.fg_bd_size==nil	then t.fg_bd_size=0 end	
	if t.fg_bd_colour==nil  then t.fg_bd_colour={{1,0xFFFF00,1}} end
	
	if t.autoscale==nil     then t.autoscale=false end
	if t.inverse==nil       then t.inverse=false end
	if t.angle==nil         then t.angle=0 end
	
	if t.bg_bd_orientation==nil then t.bg_bd_orientation="nn" end
	if t.bg_orientation==nil then t.bg_orientation="nn" end
	if t.fg_bd_orientation==nil then t.fg_bd_orientation="nn" end
	if t.fg_orientation==nil then t.fg_orientation="nn" end

    --check colours tables
	for i=1, #t.fg_colour do    
        if #t.fg_colour[i]~=3 then 
        	print ("error in fg_colour table")
        	t.fg_colour[i]={1,0x0000FF,1} 
        end
    end
	
	for i=1, #t.fg_bd_colour do    
        if #t.fg_bd_colour[i]~=3 then 
        	print ("error in fg_bd_colour table")
        	t.fg_bd_colour[i]={1,0x00FF00,1} 
        end
    end
    
	for i=1, #t.bg_colour do    
        if #t.bg_colour[i]~=3 then 
        	print ("error in background color table")
        	t.bg_colour[i]={1,0xFFFFFF,0.5} 
        end
    end    

	for i=1, #t.bg_bd_colour do    
        if #t.bg_bd_colour[i]~=3 then 
        	print ("error in background border color table")
        	t.bg_bd_colour[i]={1,0xFFFFFF,1} 
        end
    end    

    --calculate skew parameters if needed
    if t.flag_init then
	    if t.skew_x == nil then 
		    t.skew_x=0 
	    else
		    t.skew_x = math.pi*t.skew_x/180	
	    end
	    if t.skew_y == nil then 
		    t.skew_y=0
	    else
		    t.skew_y = math.pi*t.skew_y/180	
	    end
	    t.flag_init=false
	end

    cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
    cairo_set_line_join(cr,CAIRO_LINE_JOIN_ROUND)

    local matrix0 = cairo_matrix_t:create()
    cairo_save(cr)
    cairo_matrix_init (matrix0, 1,t.skew_y,t.skew_x,1,0,0)
    cairo_transform(cr,matrix0)
    
   	local ratio=t.width/t.nb_values

	cairo_translate(cr,t.x,t.y)
	cairo_rotate(cr,t.angle*math.pi/180)
	cairo_scale(cr,1,-1)

	--background
	if t.background then
	    local pts=linear_orientation(t.bg_orientation,t.width,t.height)
		pat = cairo_pattern_create_linear (pts[1],pts[2],pts[3],pts[4])
		for i=1, #t.bg_colour do
			--print ("i",i,t.colour[i][1], rgb_to_r_g_b(t.colour[i]))
		    cairo_pattern_add_color_stop_rgba (pat, t.bg_colour[i][1], rgb_to_r_g_b(t.bg_colour[i]))
		end
		cairo_set_source (cr, pat)
		cairo_rectangle(cr,0,0,t.width,t.height)	
		cairo_fill(cr)	
	end
	
    --autoscale
    cairo_save(cr)
	if t.autoscale then
		t.max= t.automax*1.1
	end
	
    local scale_x = t.width/(t.nb_values-1)
	local scale_y = t.height/t.max
	
    --define first point of the graph
	if updates-updates_gap <t.nb_values then 
		t.beg = t.beg - 1
    	--next line prevent segmentation error when conky window is redraw 
		--quicly when another window "fly" over it
		if t.beg<0 then t.beg=0 end
	else
		t.beg=0
	end
    if t.inverse then cairo_scale(cr,-1,1)
    cairo_translate(cr,-t.width,0) end

	--graph foreground
	if t.foreground then
	    local pts_fg=linear_orientation_inv(t.fg_orientation,t.width,t.height)
	    pat = cairo_pattern_create_linear (pts_fg[1],pts_fg[2],pts_fg[3],pts_fg[4])
		for i=1,#t.fg_colour,1 do
			cairo_pattern_add_color_stop_rgba (pat, 1-t.fg_colour[i][1], rgb_to_r_g_b(t.fg_colour[i]))
		end
		cairo_set_source (cr, pat)

		cairo_move_to(cr,t.beg*scale_x,0)
		cairo_line_to(cr,t.beg*scale_x,t.values[t.beg+1]*scale_y)
		for i=t.beg, t.nb_values-1 do
			cairo_line_to(cr,i*scale_x,t.values[i+1]*scale_y)		
		end
		cairo_line_to(cr,(t.nb_values-1)*scale_x,0)
		cairo_close_path(cr)
		cairo_fill(cr)
	end

	--graph_border
	if t.fg_bd_size>0 then
    	local pts=linear_orientation_inv(t.fg_bd_orientation,t.width,t.height)
		pat = cairo_pattern_create_linear (pts[1],pts[2],pts[3],pts[4])
		for i=1,#t.fg_bd_colour,1 do
			cairo_pattern_add_color_stop_rgba (pat, 1-t.fg_bd_colour[i][1], rgb_to_r_g_b(t.fg_bd_colour[i]))
		end
		cairo_set_source (cr, pat)
		cairo_move_to(cr,t.beg*scale_x,t.values[t.beg+1]*scale_y)
		for i=t.beg, t.nb_values-1 do
			cairo_line_to(cr,i*scale_x,t.values[i+1]*scale_y)		
		end
		cairo_set_line_width(cr,t.fg_bd_size)
		cairo_stroke(cr)
	end
	cairo_restore(cr)

	--background border
	
	if t.bg_bd_size>0 then
    	local pts=linear_orientation(t.bg_bd_orientation,t.width,t.height)
		pat = cairo_pattern_create_linear (pts[1],pts[2],pts[3],pts[4])
		for i=1, #t.bg_bd_colour do
			--print ("i",i,t.colour[i][1], rgb_to_r_g_b(t.colour[i]))
		    cairo_pattern_add_color_stop_rgba (pat, t.bg_bd_colour[i][1], rgb_to_r_g_b(t.bg_bd_colour[i]))
		end
		cairo_set_source (cr, pat)
		cairo_rectangle(cr,0,0,t.width,t.height)	
		cairo_set_line_width(cr,t.bg_bd_size)
		cairo_stroke(cr)	
	end	

	cairo_restore(cr)

end

```
ring.lua:
```

--[[ RINGS with SECTORS widget
	v1.0 by wlourf (08.08.2010)
	this widget draws a ring with differents effects 
	http://u-scripts.blogspot.com/2010/08/rings-sectors-widgets.html
	
To call the script in a conky, use, before TEXT
	lua_load /path/to/the/script/rings.lua
	lua_draw_hook_pre main_rings
and add one line (blank or not) after TEXT


Parameters are :
3 parameters are mandatory
name		- the name of the conky variable to display,
			  for example for {$cpu cpu0}, just write name="cpu"
arg			- the argument of the above variable,
			  for example for {$cpu cpu0}, just write arg="cpu0"
		  	  arg can be a numerical value if name=""
max			- the maximum value the above variable can reach,
			  for example for {$cpu cpu0}, just write max=100
	
Optional parameters:
xc,yc		- coordinates of the center of the ring,
			  default = middle of the conky window
radius		- external radius of the ring, in pixels,
			  default = quarter of the width of the conky window
thickness	- thickness of the ring, in pixels, default = 10 pixels
start_angle	- starting angle of the ring, in degrees, value can be negative,
			  default = 0 degree
end_angle	- ending angle of the ring, in degrees,
			  value must be greater than start_angle, default = 360 degrees
sectors		- number of sectors in the ring, default = 10
gap_sectors - gap between two sectors, in pixels, default = 1 pixel
cap			- the way to close a sector, available values are
				"p" for parallel , default value 
				"r" for radial (follow the radius)
inverse_arc	- if set to true, arc will be anticlockwise, default=false
border_size	- size of the border, in pixels, default = 0 pixel i.e. no border
fill_sector	- if set to true, each sector will be completely filled,
			  default=false, this parameter is inoperate if sectors=1
background	- if set to false, background will not be drawn, default=true
foreground	- if set to false, foreground will not be drawn, default=true

Colours tables below are defined into braces :
{position in the gradient (0 to 1), colour in hexadecimal, alpha (0 to 1)}
example for a single colour table : 
{{0,0xFFAA00,1}} position parameter doesn't matter
example for a two-colours table : 
{{0,0xFFAA00,1},{1,0x00AA00,1}} or {{0.5,0xFFAA00,1},{1,0x00AA00,1}}
example for a three-colours table : 
{{0,0xFFAA00,1},{0.5,0xFF0000,1},{1,0x00AA00,1}}

bg_colour1	- colour table for background,
			  default = {{0,0x00ffff,0.1},{0.5,0x00FFFF,0.5},{1,0x00FFFF,0.1}}
fg_colour1	- colour table for foreground,
			  default = {{0,0x00FF00,0.1},{0.5,0x00FF00,1},{1,0x00FF00,0.1}}
bd_colour1	- colour table for border,
			  default = {{0,0xFFFF00,0.5},{0.5,0xFFFF00,1},{1,0xFFFF00,0.5}}			  

Seconds tables for radials gradients :
bg_colour2	- second colour table for background, default = no second colour
fg_colour2	- second colour table for foreground, default = no second colour
bd_colour2	- second colour table for border, default = no second colour

v1.0 (08 Aug. 2010) original release

]]


require 'cairo'
function conky_main_rings()
         conky_main_bars()
         conky_draw_text()
         --conky_draw_text()
-- START PARAMETERS HERE
rings_settings={
-- MEM 

-- Mem Base Fill --
      --###Set color value 000000 to 1a1a1a when using black background!
	{
	name="",
	arg="",
	max=100,
	xc=45,
	yc=106,
	thickness=24,
	radius=24,
	start_angle=-181,
	end_angle=1,
	sectors=1,
	bg_colour2={{0,0x000000,0.25},{0.5,0x000000,0.25},{1,0x000000,0.25}},
	bg_colour1={{0,0x000000,0.25},{0.5,0x000000,0.25},{1,0x000000,0.25}},
	},

-- Mem Shadow
{
	name="",
	arg="",
	max=100,
	xc=45,
	yc=106,
	thickness=11,
	radius=35,
	start_angle=-181,
	end_angle=0,
	sectors=1,
	bg_colour2={{0,0x000000,0.25},{0.5,0x000000,0.1},{1,0x000000,0}},
	bg_colour1={{0,0x000000,0.25},{0.5,0x000000,0.1},{1,0x000000,0}},
	},
--mem
	{
	name="memperc",
	arg="",
	max=33,
	xc=45,
	yc=106,
	thickness=8,
	radius=21,
	start_angle=-180,
	end_angle=-0,
	sectors=5,
	gap_sectors=1,
	fg_colour1={{0,0X1900ff,0},{0.5,0X1900ff,1}, {1,0X1900ff,0}},
	fg_colour2={{0,0X1900ff,0},{0.5,0X1900ff,1}, {1,0X1900ff,0}},
	bg_colour2={ {0,0x1900ff,0},{0.5,0x1900ff,0.25},{1,0x1900ff,0}},
	bg_colour1={ {0,0x1900ff,0},{0.5,0x1900ff,0.25},{1,0x1900ff,0}},
	},
	     
--swap
        {
	name="swapperc",
	arg="",
	max=80,
	xc=45,
	yc=106,
	thickness=8,
	radius=12,
	start_angle=-90,
	end_angle=210,
	sectors=4,
	gap_sectors=1,
	fg_colour1={{0,0Xff0066,0},{0.7,0Xff0066,1}, {1,0Xff0066,0}},
	fg_colour2={{0,0Xff0066,0},{0.7,0Xff0066,1}, {1,0Xff0066,0}},
	bg_colour2={ {0,0xff0066,0},{0.5,0xff0066,0.25},{1,0xff0066,0}},
	bg_colour1={ {0,0xff0066,0},{0.5,0xff0066,0.25},{1,0xff0066,0}},
	},
--swap alarm--
	{
	name="",
	arg=conky_parse("${swapperc}")-80,
	max=20,
	xc=45,
	yc=106,
	thickness=8,
	radius=12,
	start_angle=210,
	end_angle=270,
	sectors=1,
	gap_sectors=1,
	fg_colour1={{0,0Xff0000,0},{0.7,0Xff0000,1}, {1,0Xff0000,0}},
	fg_colour2={{0,0Xff0000,0},{0.7,0Xff0000,1}, {1,0Xff0000,0}},
	bg_colour2={ {0,0xff0066,0},{0.5,0xff0066,0.25},{1,0xff0066,0}},
	bg_colour1={ {0,0xff0066,0},{0.5,0xff0066,0.25},{1,0xff0066,0}},
	},
---cpu1-- ##first part of ring##
	{
	name="cpu",
	arg="cpu1",
	max=67,
	xc=178,
	yc=67,
	thickness=6,
	radius=11,
	start_angle=-128,
	end_angle=90,
        inverse_arc=true,
	sectors=1,
	fill_sectors=true,
	fg_colour2={{0,0X0066ff,1},{0.5,0X0066ff,0.5},{1,0X0066ff,1}},
	fg_colour1={{0,0X9900ff,1},{0.5,0X9900ff,0.5},{1,0X9900ff,1}},
	bg_colour2={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	bg_colour1={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	},
---cpu1-- ##second part of ring##
	{
	name="",
	arg=conky_parse("${cpu  cpu1}")-67,
	max=33,
	xc=178,
	yc=67,
	thickness=6,
	radius=11,
	start_angle=127,
	end_angle=230,
        inverse_arc=true,
	sectors=3,
	fill_sectors=true,
        gap_sectors=2,
	fg_colour1={{0,0X0066ff,1},{0.5,0X0066ff,0.5},{1,0X0066ff,1}},
	fg_colour2={{0,0X9900ff,1},{0.5,0X9900ff,0.5},{1,0X9900ff,1}},
	bg_colour2={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	bg_colour1={ {0,0xffffff,0.05},{0.5,0xffffff,0},{1,0xffffff,0.05}},
	},
---cpu2-- ##first part of ring##
	{
	name="cpu",
	arg="cpu2",
	max=67,
	xc=195,
	yc=67,
	thickness=6,
	radius=11,
	start_angle=45,
	end_angle=270,
        inverse_arc=true,
	sectors=1,
	fill_sectors=true,
	fg_colour1={{0,0X0066ff,1},{0.5,0X0066ff,0.5},{1,0X0066ff,1}},
	fg_colour2={{0,0X9900ff,1},{0.5,0X9900ff,0.5},{1,0X9900ff,1}},
	bg_colour2={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	bg_colour1={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	},
---cpu2-- ##second part of ring##
	{
	name="",
	arg=conky_parse("${cpu  cpu2}")-67,
	max=33,
	xc=195,
	yc=67,
	thickness=6,
	radius=11,
	start_angle=-54,
	end_angle=42,
        inverse_arc=true,
	sectors=3,
	fill_sectors=true,
        gap_sectors=2,
	fg_colour2={{0,0X0066ff,1},{0.5,0X0066ff,0.5},{1,0X0066ff,1}},
	fg_colour1={{0,0X9900ff,1},{0.5,0X9900ff,0.5},{1,0X9900ff,1}},
	bg_colour2={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	bg_colour1={ {0,0xffffff,0.05},{0.5,0xffffff,0},{1,0xffffff,0.05}},
	},
---net up -- ##first part of ring##
	{
	name="upspeedf",
	arg="wlan0",
	max=134,
	xc=694,
	yc=67,
	thickness=6,
	radius=11,
	start_angle=-45,
	end_angle=-270,
	sectors=1,
	fill_sectors=true,
	fg_colour2={{0,0Xe5ff00,1},{0.5,0Xe5ff00,0.5},{1,0Xe5ff00,1}},
	fg_colour1={{0,0Xe5ff00,1},{0.5,0Xe5ff00,0.5},{1,0Xe5ff00,1}},
	bg_colour2={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	bg_colour1={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	},
---net up-- #Second part of ring##
	{
	name="",
	arg=conky_parse("${upspeedf wlan0}")-134,
	max=66,
	xc=694,
	yc=67,
	thickness=6,
	radius=11,
	start_angle=54,
	end_angle=-42,
	sectors=3,
	fill_sectors=true,
        gap_sectors=2,
	fg_colour1={{0,0Xff9900,1},{0.5,0Xff9900,0.5},{1,0Xff9900,1}},
	fg_colour2={{0,0Xe5ff00,1},{0.5,0Xe5ff00,0.5},{1,0Xe5ff00,1}},
	bg_colour1={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	bg_colour2={ {0,0xffffff,0.1},{0.5,0xffffff,0},{1,0xffffff,0.1}},
	},
---net down-- ##first part of ring##
	{
	name="downspeedf",
	arg="wlan0",
	max=366,
	xc=711,
	yc=67,
	thickness=6,
	radius=11,
	start_angle=128,
	end_angle=-90,
	sectors=1,
	fill_sectors=true,
	fg_colour2={{0,0X00ff19,1},{0.5,0X00ff19,0.5},{1,0X00ff19,1}},
	fg_colour1={{0,0X00ff19,1},{0.5,0X00ff19,0.5},{1,0X00ff19,1}},
	bg_colour2={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	bg_colour1={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	},
---net down-- ##second part of ring##
	{
	name="",
	arg=conky_parse("${downspeedf wlan0}")-366,
	max=184,
	xc=711,
	yc=67,
	thickness=6,
	radius=11,
	start_angle=129,
	end_angle=230,
	sectors=3,
	fill_sectors=true,
        gap_sectors=2,
	fg_colour1={{0,0Xff9900,1},{0.5,0Xff9900,0.5},{1,0Xff9900,1}},
	fg_colour2={{0,0X00ff19,1},{0.5,0X00ff19,0.5},{1,0X00ff19,1}},
	bg_colour1={ {0,0xffffff,0.3},{0.5,0xffffff,0.2},{1,0xffffff,0.3}},
	bg_colour2={ {0,0xffffff,0.1},{0.5,0xffffff,0},{1,0xffffff,0.1}},
	},
	
--GPU
--Gpu Base Fill-- ###Set color value 000000 to 1a1a1a when using black background!
{
	name="",
	arg="",
	max=100,
	xc=849,
	yc=106,
	thickness=24,
	radius=24,
	start_angle=181,
	end_angle=-1,
	sectors=1,
	bg_colour2={{0,0x000000,0.25},{1,0x000000,0.25}},
	bg_colour1={{0,0x000000,0.25},{1,0x000000,0.25}},
	},
	
--GPU Shadow 
	{
	name="",
	arg="",
	max=100,
	xc=849,
	yc=106,
	thickness=11,
	radius=35,
	start_angle=181,
	end_angle=-1,
	sectors=1,
	bg_colour2={{0,0x000000,0.25},{0.5,0x000000,0.1},{1,0x000000,0}},
	bg_colour1={{0,0x000000,0.25},{0.5,0x000000,0.1},{1,0x000000,0}},
	},
--GPU
	{
	name="",
	arg=conky_parse("${nvidia gpufreq}")-266.7,
	max=133.3,
	xc=849,
	yc=106,
	thickness=8,
	radius=21,
	start_angle=0,
	end_angle=180,
        inverse_arc=true,
	sectors=6,
	fg_colour1={{0,0xff4c94,0},{0.5,0xff4c94,1}, {1,0xff4c94,0}},
	fg_colour2={{0,0xff4c94,0},{0.5,0xff4c94,1}, {1,0xff4c94,0}},
	bg_colour2={ {0,0xff4c94,0},{0.5,0xff4c94,0.25},{1,0xff4c94,0}},
	bg_colour1={ {0,0xff4c94,0},{0.5,0xff4c94,0.25},{1,0xff4c94,0}},
	},

}
--END OF PARAMETERS HERE

--main function

	if conky_window==nil then return end

	local cs=cairo_xlib_surface_create(conky_window.display,
		conky_window.drawable, 
		conky_window.visual, conky_window.width, conky_window.height)
	cr=cairo_create(cs)

	if tonumber(conky_parse('${updates}'))>3 then
		for i in pairs(rings_settings) do
			draw_ring(rings_settings[i])
		end
	end

	cairo_destroy(cr)

end




function draw_ring(t)

	local function rgba_to_r_g_b_a(tcolour)
		colour,alpha=tcolour[2],tcolour[3]
		return ((colour / 0x10000) % 0x100) / 255., 
			((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end
			
			
	local function calc_delta(tcol1,tcol2)
		--calculate deltas P R G B A to table_colour 1

		for x = 1, #tcol1 do
			tcol1[x].dA	= 0
			tcol1[x].dP = 0
	 		tcol1[x].dR = 0
			tcol1[x].dG = 0
			tcol1[x].dB = 0
			if tcol2~=nil and #tcol1 == #tcol2 then
				local r1,g1,b1,a1 = rgba_to_r_g_b_a(tcol1[x])
				local r2,g2,b2,a2 = rgba_to_r_g_b_a(tcol2[x])
				tcol1[x].dP = (tcol2[x][1]-tcol1[x][1])/t.sectors
		 		tcol1[x].dR = (r2-r1)/t.sectors
				tcol1[x].dG = (g2-g1)/t.sectors
				tcol1[x].dB = (b2-b1)/t.sectors
				tcol1[x].dA = (a2-a1)/t.sectors		
				
			end
		end
		
		return tcol1
	end

	--check values
	local function setup(t)
		if t.name==nil and t.arg==nil then 
			print ("No input values ... use parameters 'name'" +
				" with 'arg' or only parameter 'arg' ") 
			return
		end

		if t.max==nil then
			print ("No maximum value defined, use 'max'")
			print ("for name=" .. t.name)
			print ("with arg=" .. t.arg)
			return
		end
		if t.name==nil then t.name="" end
		if t.arg==nil then t.arg="" end

		if t.xc==nil then t.xc=conky_window.width/2 end
		if t.yc==nil then t.yc=conky_window.height/2 end
		if t.thickness ==nil then t.thickness = 10 end
		if t.radius ==nil then t.radius =conky_window.width/4 end
		if t.start_angle==nil then t.start_angle =0 end
		if t.end_angle==nil then t.end_angle=360 end
		if t.bg_colour1==nil then 
			t.bg_colour1={{0,0x00ffff,0.1},{0.5,0x00FFFF,0.5},{1,0x00FFFF,0.1}}
		end
		if t.fg_colour1==nil then
			t.fg_colour1={{0,0x00FF00,0.1},{0.5,0x00FF00,1},{1,0x00FF00,0.1}}
		end
		if t.bd_colour1==nil then
			t.bd_colour1={{0,0xFFFF00,0.5},{0.5,0xFFFF00,1},{1,0xFFFF00,0.5}}
		end
		if t.sectors==nil then t.sectors=10 end
		if t.gap_sectors==nil then t.gap_sectors=1 end 
		if t.fill_sector==nil then t.fill_sector=false end
		if t.sectors==1 then t.fill_sector=false end
		if t.border_size==nil then t.border_size=0 end
		if t.cap==nil then t.cap="p" end
		--some checks
		if t.thickness>t.radius then t.thickness=t.radius*0.1 end
		t.int_radius = t.radius-t.thickness

		--check colors tables 
		for i=1, #t.bg_colour1 do 
			if #t.bg_colour1[i]~=3 then t.bg_colour1[i]={1,0xFFFFFF,0.5} end
		end
		for i=1, #t.fg_colour1 do 
			if #t.fg_colour1[i]~=3 then t.fg_colour1[i]={1,0xFF0000,1} end
		end
		for i=1, #t.bd_colour1 do 
			if #t.bd_colour1[i]~=3 then t.bd_colour1[i]={1,0xFFFF00,1} end
		end
	
		if t.bg_colour2~=nil then
			for i=1, #t.bg_colour2 do 
				if #t.bg_colour2[i]~=3 then t.bg_colour2[i]={1,0xFFFFFF,0.5} end
			end
		end
		if t.fg_colour2~=nil then
			for i=1, #t.fg_colour2 do 
				if #t.fg_colour2[i]~=3 then t.fg_colour2[i]={1,0xFF0000,1} end
			end
		end
		if t.bd_colour2~=nil then
			for i=1, #t.bd_colour2 do 
				if #t.bd_colour2[i]~=3 then t.bd_colour2[i]={1,0xFFFF00,1} end
			end
		end 	
		
		if t.start_angle>=t.end_angle then
		 local tmp_angle=t.end_angle
		 t.end_angle= t.start_angle
		 t.start_angle = tmp_angle
		 -- print ("inversed angles")
			if t.end_angle-t.start_angle>360 and t.start_angle>0 then
				t.end_angle=360+t.start_angle
				print ("reduce angles")
			end
		
			if t.end_angle+t.start_angle>360 and t.start_angle<=0 then
				t.end_angle=360+t.start_angle
				print ("reduce angles")
			end
		
			if t.int_radius<0 then t.int_radius =0 end
			if t.int_radius>t.radius then
				local tmp_radius=t.radius
				t.radius=t.int_radius
				t.int_radius=tmp_radius
				print ("inversed radius")
			end
			if t.int_radius==t.radius then
				t.int_radius=0
				print ("int radius set to 0")
			end 
		end
		
		t.fg_colour1 = calc_delta(t.fg_colour1,t.fg_colour2)
		t.bg_colour1 = calc_delta(t.bg_colour1,t.bg_colour2)
		t.bd_colour1 = calc_delta(t.bd_colour1,t.bd_colour2)
	end
	
	--initialize table
	setup(t)
	--[[grid
	h=conky_window.height
	w=conky_window.width
	cairo_set_source_rgba(cr,1,1,1,1)
	cairo_set_line_width(cr,0.5)
	cairo_move_to(cr,0,t.yc)
	cairo_line_to(cr,w,t.yc)
	cairo_stroke(cr)
	cairo_move_to(cr,t.xc,0)
	cairo_line_to(cr,t.xc,h)
	cairo_stroke(cr)
	cairo_move_to(cr,t.xc,t.yc)
	cairo_line_to(cr,t.xc+200*math.sin(math.pi/4),t.yc-200*math.cos(math.pi/4))
	cairo_stroke(cr)
	cairo_move_to(cr,0,t.yc-t.radius)
	cairo_line_to(cr,w,t.yc-t.radius)
	cairo_stroke(cr)
	cairo_move_to(cr,0,t.yc-t.int_radius)
	cairo_line_to(cr,w,t.yc-t.int_radius)
	cairo_stroke(cr)
	cairo_move_to(cr,0,t.yc-t.gap_sectors)
	cairo_line_to(cr,w,t.yc-t.gap_sectors)
	cairo_stroke(cr)
	cairo_set_source_rgba(cr,1,0,0,0.5)
	cairo_arc(cr,t.xc,t.yc,t.radius,0,2*math.pi)
	cairo_stroke(cr)
	cairo_arc(cr,t.xc,t.yc,t.int_radius,0,2*math.pi)	
	cairo_stroke(cr)	
	cairo_set_source_rgba(cr,0,1,0,1)	
	cairo_move_to(cr,t.xc+t.gap_sectors,t.yc-t.gap_sectors)
	cairo_line_to(cr,t.xc+400*math.sin(math.pi/4),t.yc-400*math.cos(math.pi/4))
	cairo_stroke(cr)
	--END GRID
	]]
	
	--initialize cairo context
	cairo_save(cr)
	cairo_translate(cr,t.xc,t.yc)
	cairo_set_line_join (cr, CAIRO_LINE_JOIN_ROUND)
	cairo_set_line_cap (cr, CAIRO_LINE_CAP_ROUND)

	--get value
	local value = 0
	if t.name ~="" then
		value = tonumber(conky_parse(string.format('${%s %s}', t.name, t.arg)))
	else
		value = tonumber(t.arg)
	end
	if value==nil then value =0 end

	--initialize sectors
	--angle of a sector :
	angleA = ((t.end_angle-t.start_angle)/t.sectors)*math.pi/180
	--value of a sector : 
	valueA = t.max/t.sectors
	--first angle of a sector : 
	lastAngle = t.start_angle*math.pi/180


	local function draw_sector(type_arc,angle0,angle,valpc, idx)
	 
		--this function draws a portion of arc
	 	--type of arc, angle0 = strating angle, angle= angle of sector,
	 	--valpc = percentage inside the sector, idx = sctor number #
		 if type_arc=="bg" then 		--background
			 if valpc==1 then return end
		 	tcolor=t.bg_colour1
		 elseif type_arc=="fg" then	--foreground
		 	if valpc==0 then return end
		 	tcolor=t.fg_colour1
		 elseif type_arc=="bd" then	--border
		 	tcolor=t.bd_colour1
		 end 

		--angles equivalents to gap_sector
		local ext_delta=math.atan(t.gap_sectors/(2*t.radius))
		local int_delta=math.atan(t.gap_sectors/(2*t.int_radius))

		--angles of arcs
		local ext_angle=(angle-ext_delta*2)*valpc
		local int_angle=(angle-int_delta*2)*valpc

		--define colours to use for this sector
		if #tcolor==1 then 
			--plain color
			local vR,vG,vB,vA = rgba_to_r_g_b_a(tcolor[1])
			cairo_set_source_rgba(cr,vR+tcolor[1].dR*idx,
									vG+tcolor[1].dG*idx,
									vB+tcolor[1].dB*idx,
									vA+tcolor[1].dA*idx	)
		else
			--radient color
			local pat=cairo_pattern_create_radial(0,0,t.int_radius,0,0,t.radius)
			for i=1, #tcolor do
				local vP,vR,vG,vB,vA = tcolor[i][1], rgba_to_r_g_b_a(tcolor[i])
				cairo_pattern_add_color_stop_rgba (pat, 
									vP+tcolor[i].dP*idx,
									vR+tcolor[i].dR*idx,
									vG+tcolor[i].dG*idx,
									vB+tcolor[i].dB*idx,
									vA+tcolor[i].dA*idx	)
			end
			cairo_set_source (cr, pat)
			cairo_pattern_destroy(pat)
		end

		--start drawing
		 cairo_save(cr)
		--x axis is parrallel to start of sector
		cairo_rotate(cr,angle0-math.pi/2)

		local ri,re = t.int_radius ,t.radius

		--point A 
		local angle_a
	
		if t.cap == "p" then 
			angle_a = int_delta
			if t.inverse_arc and type_arc ~="bg" then
				angle_a = angle-int_angle-int_delta
			end
			if not(t.inverse_arc) and type_arc =="bg" then
				angle_a = int_delta+int_angle
			end
		else --t.cap=="r"
			angle_a = ext_delta
			if t.inverse_arc and type_arc~="bg" then
				angle_a = angle-ext_angle-ext_delta
			end
			if not(t.inverse_arc) and type_arc=="bg" then
				angle_a = ext_delta+ext_angle
			end
		end
		local ax,ay = ri*math.cos(angle_a),ri*math.sin(angle_a)


		--point B
		local angle_b = ext_delta
		if t.cap == "p" then 
			if t.inverse_arc and type_arc ~="bg" then
				angle_b = angle-ext_angle-ext_delta
			end
			if not(t.inverse_arc) and type_arc=="bg" then
				angle_b = ext_delta+ext_angle
			end
		else
			if t.inverse_arc and type_arc ~="bg" then
				angle_b = angle-ext_angle-ext_delta
			end
			if not(t.inverse_arc) and type_arc=="bg" then
				angle_b = ext_delta+ext_angle
			end
		end
		local bx,by = re*math.cos(angle_b),re*math.sin(angle_b)

		-- EXTERNAL ARC B --> C
		if t.inverse_arc then
			if type_arc=="bg" then
				b0,b1= ext_delta, angle-ext_delta-ext_angle
			else
				b0,b1= angle-ext_angle-ext_delta, angle-ext_delta
			end
		else
			if type_arc=="bg" then
				b0,b1= ext_delta+ext_angle, angle-ext_delta
			else
				b0,b1= ext_delta, ext_angle+ext_delta
			end
		end
		
		---POINT D
		local angle_c 
		if t.cap == "p" then 
			angle_d = angle-int_delta
			if t.inverse_arc and type_arc=="bg" then
				angle_d = angle-int_delta-int_angle	
			end
			if not(t.inverse_arc) and type_arc~="bg" then
				angle_d=int_delta+int_angle
			end
		else
			angle_d = angle-ext_delta
			if t.inverse_arc and type_arc=="bg" then
				angle_d =angle-ext_delta-ext_angle
			end
			if not(t.inverse_arc) and type_arc~="bg" then
				angle_d = ext_angle+ext_delta
			end
		end
		local dx,dy = ri*math.cos(angle_d),ri*math.sin(angle_d)
		
		-- INTERNAL ARC D --> A
		if t.cap=="p" then	
			if t.inverse_arc then	
				if type_arc=="bg" then
					d0,d1= angle-int_delta-int_angle,int_delta
				else
					d0,d1= angle-int_delta, angle- int_angle-int_delta
				end
			else
				if type_arc=="bg" then
					d0,d1= angle-int_delta, int_delta+int_angle
				else
					d0,d1= int_delta+int_angle, int_delta
				end
			end
		else
			if t.inverse_arc then	
				if type_arc=="bg" then	
					d0,d1= angle-ext_delta-ext_angle,ext_delta
				else
					d0,d1= angle-ext_delta, angle- ext_angle-ext_delta
				end
			else
				if type_arc=="bg" then	
					d0,d1= angle-ext_delta,ext_delta+ext_angle
				else	
					d0,d1= ext_angle+ext_delta, ext_delta
				end
			end			
		end
			
		--draw sector
		cairo_move_to(cr,ax,ay)
		cairo_line_to(cr,bx,by)
		cairo_arc(cr,0,0,re,b0,b1)
		cairo_line_to(cr,dx,dy) 
		cairo_arc_negative(cr,0,0,ri,d0,d1)
		 cairo_close_path (cr);

		--stroke or fill sector
		 if type_arc=="bd" then
		 	cairo_set_line_width(cr,t.border_size)
		 	cairo_stroke(cr)
		 else
			 cairo_fill(cr)
		 end

		 cairo_restore(cr)

	 end
	--draw sectors
	local n0,n1,n2 = 1,t.sectors,1
	if t.inverse_arc then n0,n1,n2 = t.sectors,1,-1 end
	local index = 0
	for i = n0,n1,n2 do 
		index = index +1
		local valueZ=1
		local cstA, cstB = (i-1),i
		if t.inverse_arc then cstA,cstB = (t.sectors-i), (t.sectors-i+1) end
		
		if value>valueA *cstA and value<valueA*cstB then
			if not t.fill_sector then
				valueZ = (value-valueA*cstA)/valueA
			end
		else
			if value<valueA*cstB then valueZ=0 end
		end
		
		local start_angle= lastAngle+(i-1)*angleA
		if t.foreground ~= false then 
			draw_sector("fg",start_angle,angleA,valueZ, index)
		end
		if t.background ~= false then 
			draw_sector("bg",start_angle,angleA,valueZ, i)
		end
		if t.border_size>0 then draw_sector("bd",start_angle,angleA,1, i) end
	end

	cairo_restore(cr)
end


--[[END OF RING-SECTORS WIDGET]]
function clock_hands(xc, yc, colour, alpha, show_secs, size)
	
--[[ Options (xc, yc, colour, alpha, show_secs, size):
	"xc" and "yc" are the x and y coordinates of the centre of the clock hands, in pixels, relative to the top left corner of the Conky window
	"colour" is the colour of the clock hands, in Ox33312c formate
	"alpha" is the alpha of the hands, between 0 and 1
	"show_secs" is a boolean; set to TRUE to show the seconds hand, otherwise set to FALSE
	"size" is the total size of the widget (e.g. twice the length of the minutes hand), in pixels ]]
	
	local secs,mins,hours,secs_arc,mins_arc,hours_arc
	local xh,yh,xm,ym,xs,ys

	secs=os.date("%S")
	mins=os.date("%M")
	hours=os.date("%I")

	secs_arc=(2*math.pi/60)*secs
	mins_arc=(2*math.pi/60)*mins+secs_arc/60
	hours_arc=(2*math.pi/12)*hours+mins_arc/12

	xh=xc+0.4*size*math.sin(hours_arc)
	yh=yc-0.4*size*math.cos(hours_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xh,yh)

	cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
	cairo_set_line_width(cr,5)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(colour,alpha))
	cairo_stroke(cr)

	xm=xc+0.5*size*math.sin(mins_arc)
	ym=yc-0.5*size*math.cos(mins_arc)
	cairo_move_to(cr,xc,yc)
	cairo_line_to(cr,xm,ym)

	cairo_set_line_width(cr,3)
	cairo_stroke(cr)

	if show_secs then
		xs=xc+0.5*size*math.sin(secs_arc)
		ys=yc-0.5*size*math.cos(secs_arc)
		cairo_move_to(cr,xc,yc)
		cairo_line_to(cr,xs,ys)

		cairo_set_line_width(cr,1)
		cairo_stroke(cr)
	end

	cairo_set_line_cap(cr,CAIRO_LINE_CAP_BUTT)
end

--[[ END CLOCK HANDS WIDGET ]]

function axis(ctx,alpha)
	cairo_set_line_width(ctx,1)
	cairo_set_source_rgba(ctx,1,0,0,alpha)
	cairo_move_to(ctx,0,0)
	cairo_line_to(ctx,150,0)
	cairo_stroke(ctx)
	cairo_set_source_rgba(ctx,0,1,0,alpha)
	cairo_move_to(ctx,0,0)
	cairo_line_to(ctx,0,150)
	cairo_stroke(ctx)
end
```
bargraph1.lua:
```


--[[ BARGRAPH WIDGET
	v2.0 by wlourf (12.07.2010)
	this widget draws a bargraph with differe,ts effects 
	http://u-scripts.blogspot.com/2010/07/bargraph-widget.html
	
	
Parameters are :
3 parameters are mandatory
name	- the name of the conky variable to display, for example for {$cpu cpu0}, just write name="cpu"
arg		- the argument of the above variable, for example for {$cpu cpu0}, just write arg="cpu0"
		  arg can be a numericla value if name=""
max		- the maximum value the above variable can reach, for example for {$cpu cpu0}, just write  max=100
	
Optional parameters:
x,y		- coordinates of the starting point of the bar, default = middle of the conky window
cap		- end of cap line, ossibles values are r,b,s (for round, butt, square), default="b"
		  http://www.cairographics.org/samples/set_line_cap/
angle	- angle of rotation of the bar in degress, default = 0 (i.e. a vertical bar)
		  set to 90 for an horizontal bar
skew_x	- skew bar around x axis, défaut = 0
skew_y	- skew bar around y axis, défaut = 0
blocks  - number of blocks to display for a bar (values >0) , default= 10
height	- height of a block, default=10 pixels
width	- width of a block, default=20 pixels
space	- space between 2 blocks, default=2 pixels
angle_bar	- this angle is used to draw a bar on a circular way (ok, this is no more a bar !) default=0
radius		- for cicular bars, internal radius, default=0
			  with radius, parameter width has no more effect.

Colours below are defined into braces {colour in hexadecimal, alpha}
fg_colour	- colour of a block ON, default= {0x00FF00,1}
bg_colour	- colour of a block OFF, défaut = {0x00FF00,0.5}
alarm		- threshold, values after this threshold will use alarm_colour colour , default=max
alarm_colour - colour of a block greater than alarm, default=fg_colour
smooth		- (true or false), create a gradient from fg_colour to bg_colour, default=false 
mid_colour	- colours to add to gradient, with this syntax {position into the gradient (0 to1), colour hexa, alpha}
			  for example, this table {{0.25,0xff0000,1},{0.5,0x00ff00,1},{0.75,0x0000ff,1}} will add
			  3 colurs to gradient created by fg_colour and alarm_colour, default=no mid_colour
led_effect	- add LED effects to each block, default=no led_effect
			  if smooth=true, led_effect is not used
			  possibles values : "r","a","e" for radial, parallelel, perdendicular to the bar (just try!)
			  led_effect has to be used with theses colours :
fg_led		- middle colour of a block ON, default = fg_colour
bg_led		- middle colour of a block OFF, default = bg_colour
alarm_led	- middle colour of a block > ALARM,  default = alarm_colour

reflection parameters, not avaimable for circular bars
reflection_alpha    - add a reflection effect (values from 0 to 1) default = 0 = no reflection
                      other values = starting opacity
reflection_scale    - scale of the reflection (default = 1 = height of text)
reflection_length   - length of reflection, define where the opacity will be set to zero
					  calues from 0 to 1, default =1
reflection			- position of reflection, relative to a vertical bar, default="b"
					  possibles values are : "b","t","l","r" for bottom, top, left, right


v1.0 (10 Feb. 2010) original release
v1.1 (13 Feb. 2010) numeric values can be passed instead conky stats with parameters name="", arg = numeric_value	
v1.2 (28 Feb. 2010) just renamed the widget to bargraph
v1.3 (03 March 2010) added parameters radius & angle_bar to draw the bar in a circular way
v2.0 (12 Jul. 2010) rewrite script + add reflection effects and parameters are now set into tables
]]

require 'cairo'

----------------START OF PARAMETERS ----------
function conky_main_bars()
	bars_settings={
--MEM starts with ring meets into this bar
		{
			name="",
			arg=conky_parse("${memperc}")-33,
			max=67,
			alarm=57,
			angle=90,
			height=8.3,
			width=8,
			space=1,
			bg_colour = {0x1900ff,0},
			fg_colour = {0X1900ff,0},
			alarm_colour={0xff0000,0},
			led_effect="e",
			bg_led	={0x1900ff,0.25},
			fg_led	={0x1900ff,1},
			alarm_led={0xff0000,1},
			x=49,y=89,

		},
--GPU Feq bar start meets in with Gpu ring
		{
			name="nvidia",
			arg="gpufreq",
			max=266.7,
			angle=90,
			height=7,
			width=8,
			space=1,
			bg_colour = {0xff4c94,0},
			fg_colour = {0Xff4c94,0},
			led_effect="e",
			bg_led	={0xff4c94,0.25},
			fg_led	={0xff4c94,1},
			x=773,y=123,

		},
		--Cpu Temp
		{
			name="exec",
			arg="sensors | grep 'temp2' | cut -c15-16",
			max=105,
			alarm=90,
			bg_colour={0xff9900,0},
			fg_colour={0xff9900,0},
			alarm_colour={0xff0000,0},
			x=150,y=126,
			blocks=8,
			height=2.3,width=11,
			led_effect="r",
			fg_led={0xff9900,1},
			alarm_led={0xff0000,1},
			bg_led={0xff9900,0.25},
		},	
		
		--Gpu Temp
		{
			name="nvidia",
			arg="temp",
			max=105,
			alarm=90,
			bg_colour={0xff9900,0},
			fg_colour={0xff9900,0},
			alarm_colour={0xff0000,0},
			x=752,y=126,
			blocks=8,
			height=2.3,width=11,
			led_effect="r",
			fg_led={0xff9900,1},
			alarm_led={0xff0000,1},
			bg_led={0xff9900,0.25},
		},	
			}
	
-----------END OF PARAMETERS--------------


    
	if conky_window == nil then return end
	
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	
	cr = cairo_create(cs)    
	--prevent segmentation error when reading cpu state
    if tonumber(conky_parse('${updates}'))>3 then
        for i in pairs(bars_settings) do
        	
        	draw_multi_bar_graph(bars_settings[i])
        	
        end
    end
	cairo_destroy(cr)
	cairo_surface_destroy(cs)

end



function draw_multi_bar_graph(t)
	cairo_save(cr)
	--check values
	if t.name==nil and t.arg==nil then 
		print ("No input values ... use parameters 'name' with 'arg' or only parameter 'arg' ") 
		return
	end
	if t.max==nil then
		print ("No maximum value defined, use 'max'")
		return
	end
	if t.name==nil then t.name="" end
	if t.arg==nil then t.arg="" end

	--set default values	
	if t.x == nil		then t.x = conky_window.width/2 end
	if t.y == nil		then t.y = conky_window.height/2 end
	if t.blocks == nil	then t.blocks=10 end
	if t.height == nil	then t.height=10 end
	if t.angle == nil 	then t.angle=0 end
	t.angle = t.angle*math.pi/180
	--line cap style
	if t.cap==nil		then t.cap = "b" end
	local cap="b"
	for i,v in ipairs({"s","r","b"}) do 
		if v==t.cap then cap=v end
	end
	delta=0
	if t.cap=="r" or t.cap=="s" then delta = t.height end
	if cap=="s" then 	cap = CAIRO_LINE_CAP_SQUARE
	elseif cap=="r" then
		cap = CAIRO_LINE_CAP_ROUND
	elseif cap=="b" then
		cap = CAIRO_LINE_CAP_BUTT
	end
	--end line cap style
	--if t.led_effect == nil	then t.led_effect="r" end
	if t.width == nil	then t.width=20 end
	if t.space == nil	then t.space=2 end
	if t.radius == nil	then t.radius=0 end
	if t.angle_bar == nil	then t.angle_bar=0 end
	t.angle_bar = t.angle_bar*math.pi/360 --halt angle
	
	--colours
	if t.bg_colour == nil 	then t.bg_colour = {0x00FF00,0.5} end
	if #t.bg_colour~=2 		then t.bg_colour = {0x00FF00,0.5} end
	if t.fg_colour == nil 	then t.fg_colour = {0x00FF00,1} end
	if #t.fg_colour~=2 		then t.fg_colour = {0x00FF00,1} end
	if t.alarm_colour == nil 	then t.alarm_colour = t.fg_colour end
	if #t.alarm_colour~=2 		then t.alarm_colour = t.fg_colour end

	if t.mid_colour ~= nil then	
		for i=1, #t.mid_colour do    
		    if #t.mid_colour[i]~=3 then 
		    	print ("error in mid_color table")
		    	t.mid_colour[i]={1,0xFFFFFF,1} 
		    end
		end
    end
    
	if t.bg_led ~= nil and #t.bg_led~=2	then t.bg_led = t.bg_colour end
	if t.fg_led ~= nil and #t.fg_led~=2	then t.fg_led = t.fg_colour end
	if t.alarm_led~= nil and #t.alarm_led~=2 then t.alarm_led = t.fg_led end
	
	if t.led_effect~=nil then
		if t.bg_led == nil then t.bg_led = t.bg_colour end
		if t.fg_led == nil 	then t.fg_led = t.fg_colour end
		if t.alarm_led == nil  then t.alarm_led = t.fg_led end
	end
	

	if t.alarm==nil then t.alarm = t.max end --0.8*t.max end
	if t.smooth == nil then t.smooth = false end

	if t.skew_x == nil then 
		t.skew_x=0 
	else
		t.skew_x = math.pi*t.skew_x/180	
	end
	if t.skew_y == nil then 
		t.skew_y=0
	else
		t.skew_y = math.pi*t.skew_y/180	
	end
	
	if t.reflection_alpha==nil then t.reflection_alpha=0 end
	if t.reflection_length==nil then t.reflection_length=1 end
	if t.reflection_scale==nil then t.reflection_scale=1 end
	
	--end of default values
	

 	local function rgb_to_r_g_b(col_a)
		return ((col_a[1] / 0x10000) % 0x100) / 255., ((col_a[1] / 0x100) % 0x100) / 255., (col_a[1] % 0x100) / 255., col_a[2]
	end
	
	
	--functions used to create patterns

	local function create_smooth_linear_gradient(x0,y0,x1,y1)
		local pat = cairo_pattern_create_linear (x0,y0,x1,y1)
		cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
		cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
		if t.mid_colour ~=nil then
			for i=1, #t.mid_colour do
				cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
			end
		end
		return pat
	end

	local function create_smooth_radial_gradient(x0,y0,r0,x1,y1,r1)
		local pat =  cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
		cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
		cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
		if t.mid_colour ~=nil then
			for i=1, #t.mid_colour do
				cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
			end
		end
		return pat
	end
	
	local function create_led_linear_gradient(x0,y0,x1,y1,col_alp,col_led)
		local pat = cairo_pattern_create_linear (x0,y0,x1,y1) ---delta, 0,delta+ t.width,0)
		cairo_pattern_add_color_stop_rgba (pat, 0.0, rgb_to_r_g_b(col_alp))
		cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
		cairo_pattern_add_color_stop_rgba (pat, 1.0, rgb_to_r_g_b(col_alp))
		return pat
	end

	local function create_led_radial_gradient(x0,y0,r0,x1,y1,r1,col_alp,col_led,mode)
		local pat = cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
		if mode==3 then
			cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_alp))				
			cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
			cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))				
		else
			cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_led))
			cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))				
		end
		return pat
	end






	local function draw_single_bar()
		--this fucntion is used for bars with a single block (blocks=1) but 
		--the drawing is cut in 3 blocks : value/alarm/background
		--not zvzimzblr for circular bar
		local function create_pattern(col_alp,col_led,bg)
			local pat
			
			if not t.smooth then
				if t.led_effect=="e" then
					pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
				elseif t.led_effect=="a" then
					pat = create_led_linear_gradient (t.width/2, 0,t.width/2,-t.height,col_alp,col_led)
				elseif  t.led_effect=="r" then
					pat = create_led_radial_gradient (t.width/2, -t.height/2, 0, t.width/2,-t.height/2,t.height/1.5,col_alp,col_led,2)
				else
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
				end
			else
				if bg then
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
				else
					pat = create_smooth_linear_gradient(t.width/2, 0, t.width/2,-t.height)
				end
			end
			return pat
		end
		
		local y1=-t.height*pct/100
		local y2=nil
		if pct>(100*t.alarm/t.max) then 
			y1 = -t.height*t.alarm/100
			y2 = -t.height*pct/100
			if t.smooth then y1=y2 end
		end
		
		if t.angle_bar==0 then
		
			--block for fg value
			pat = create_pattern(t.fg_colour,t.fg_led,false)
			cairo_set_source(cr,pat)
			cairo_rectangle(cr,0,0,t.width,y1)
			cairo_fill(cr)
		
			-- block for alarm value			
			if not t.smooth and y2 ~=nil then 
				pat = create_pattern(t.alarm_colour,t.alarm_led,false)
				cairo_set_source(cr,pat)
				cairo_rectangle(cr,0,y1,t.width,y2-y1)
				cairo_fill(cr)
				y3=y2
			else
				y2,y3=y1,y1
			end
			-- block for bg value
			cairo_rectangle(cr,0,y2,t.width,-t.height-y3)
			pat = create_pattern(t.bg_colour,t.bg_led,true)
			cairo_set_source(cr,pat)
			cairo_pattern_destroy(pat)
			cairo_fill(cr)
		end		
	end  --end single bar
	





	local function draw_multi_bar()
		--function used for bars with 2 or more blocks
		for pt = 1,t.blocks do 
			--set block y
			local y1 = -(pt-1)*(t.height+t.space)
			local light_on=false
			
			--set colors
			local col_alp = t.bg_colour
			local col_led = t.bg_led
			if pct>=(100/t.blocks) or pct>0 then --ligth on or not the block
				if pct>=(pcb*(pt-1))  then 
					light_on = true
					col_alp = t.fg_colour
					col_led = t.fg_led
					if pct>=(100*t.alarm/t.max) and (pcb*pt)>(100*t.alarm/t.max) then 
						col_alp = t.alarm_colour 
						col_led = t.alarm_led 
					end
				end
			end

			--set colors
			--have to try to create gradients outside the loop ?
			local pat 
			
			if not t.smooth then
				if t.angle_bar==0 then
					if t.led_effect=="e" then
						pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
					elseif t.led_effect=="a" then
						pat = create_led_linear_gradient (t.width/2, -t.height/2+y1,t.width/2,0+t.height/2+y1,col_alp,col_led)					
					elseif  t.led_effect=="r" then
						pat = create_led_radial_gradient (t.width/2, y1, 0, t.width/2,y1,t.width/1.5,col_alp,col_led,2)	
					else
						pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
					end
				else
					 if t.led_effect=="a"  then
						 pat = create_led_radial_gradient (0, 0, t.radius+(t.height+t.space)*(pt-1),
														 0, 0, t.radius+(t.height+t.space)*(pt),						 
											 col_alp,col_led,3)	
					else
						pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))					
					end
					
				end
			else
				
				if light_on then
					if t.angle_bar==0 then
						pat = create_smooth_linear_gradient(t.width/2, t.height/2, t.width/2,-(t.blocks-0.5)*(t.height+t.space))
					else
						pat = create_smooth_radial_gradient(0, 0, (t.height+t.space),  0,0,(t.blocks+1)*(t.height+t.space),2)
					end
				else		
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
				end
			end
			cairo_set_source (cr, pat)
			cairo_pattern_destroy(pat)

			--draw a block
			if t.angle_bar==0 then
				cairo_move_to(cr,0,y1)
				cairo_line_to(cr,t.width,y1)
			else		
				cairo_arc( cr,0,0,
					t.radius+(t.height+t.space)*(pt)-t.height/2,
					 -t.angle_bar -math.pi/2 ,
					 t.angle_bar -math.pi/2)
			end
			cairo_stroke(cr)
		end	
	end
	
	
	
	
	local function setup_bar_graph()
		--function used to retrieve the value to display and to set the cairo structure
		if t.blocks ~=1 then t.y=t.y-t.height/2 end
		
		local value = 0
		if t.name ~="" then
			value = tonumber(conky_parse(string.format('${%s %s}', t.name, t.arg)))
		else
			value = tonumber(t.arg)
		end

		if value==nil then value =0 end
		
		pct = 100*value/t.max
		pcb = 100/t.blocks
		
		cairo_set_line_width (cr, t.height)
		cairo_set_line_cap  (cr, cap)
		cairo_translate(cr,t.x,t.y)
		cairo_rotate(cr,t.angle)

		local matrix0 = cairo_matrix_t:create()
		cairo_matrix_init (matrix0, 1,t.skew_y,t.skew_x,1,0,0)
		cairo_transform(cr,matrix0)

	
		
		--call the drawing function for blocks
		if t.blocks==1 and t.angle_bar==0 then
			draw_single_bar()
			if t.reflection=="t" or t.reflection=="b" then cairo_translate(cr,0,-t.height) end
		else
			draw_multi_bar()
		end

		--dot for reminder
		--[[
		if t.blocks ~=1 then
			cairo_set_source_rgba(cr,1,0,0,1)
			cairo_arc(cr,0,t.height/2,3,0,2*math.pi)
			cairo_fill(cr)
		else
			cairo_set_source_rgba(cr,1,0,0,1)
			cairo_arc(cr,0,0,3,0,2*math.pi)
			cairo_fill(cr)
		end
]]
		--call the drawing function for reflection and prepare the mask used		
		if t.reflection_alpha>0 and t.angle_bar==0 then
			local pat2
			local matrix1 = cairo_matrix_t:create()
			if t.angle_bar==0 then
				pts={-delta/2,(t.height+t.space)/2,t.width+delta,-(t.height+t.space)*(t.blocks)}
				if t.reflection=="t" then
					cairo_matrix_init (matrix1,1,0,0,-t.reflection_scale,0,-(t.height+t.space)*(t.blocks-0.5)*2*(t.reflection_scale+1)/2)
					pat2 = cairo_pattern_create_linear (t.width/2,-(t.height+t.space)*(t.blocks),t.width/2,(t.height+t.space)/2)
				elseif t.reflection=="r" then
					cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,delta+2*t.width,0)
					pat2 = cairo_pattern_create_linear (delta/2+t.width,0,-delta/2,0)
				elseif t.reflection=="l" then
					cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,-delta,0)
					pat2 = cairo_pattern_create_linear (-delta/2,0,delta/2+t.width,-0)
				else --bottom
					cairo_matrix_init (matrix1,1,0,0,-1*t.reflection_scale,0,(t.height+t.space)*(t.reflection_scale+1)/2)
					pat2 = cairo_pattern_create_linear (t.width/2,(t.height+t.space)/2,t.width/2,-(t.height+t.space)*(t.blocks))
				end
			end
			cairo_transform(cr,matrix1)

			if t.blocks==1 and t.angle_bar==0 then
				draw_single_bar()
				cairo_translate(cr,0,-t.height/2) 
			else
				draw_multi_bar()
			end
			
			
			cairo_set_line_width(cr,0.01)
			cairo_pattern_add_color_stop_rgba (pat2, 0,0,0,0,1-t.reflection_alpha)
			cairo_pattern_add_color_stop_rgba (pat2, t.reflection_length,0,0,0,1)
			if t.angle_bar==0 then
				cairo_rectangle(cr,pts[1],pts[2],pts[3],pts[4])
			end
			cairo_clip_preserve(cr)
			cairo_set_operator(cr,CAIRO_OPERATOR_CLEAR)
			cairo_stroke(cr)
			cairo_mask(cr,pat2)
			cairo_pattern_destroy(pat2)
			cairo_set_operator(cr,CAIRO_OPERATOR_OVER)
			
		end --reflection
		
		
	end --setup_bar_graph()

	
	--start here !
	setup_bar_graph()
	cairo_restore(cr)
end

```
text.lua(this one really uses recources!!!)
```
--[[TEXT WIDGET v1.3 by Wlourf 25/06/2010
This widget can drawn texts set in the "text_settings" table with some parameters
http://u-scripts.blogspot.com/2010/06/text-widget.html

The parameters (all optionals) are :
text        - text to display, default = "Conky is good for you"
			  use conky_parse to display conky value ie text=conly_parse("${cpu cpu1}")
            - coordinates below are relative to top left corner of the conky window
x           - x coordinate of first letter (bottom-left), default = center of conky window
y           - y coordinate of first letter (bottom-left), default = center of conky window
h_align		- horizontal alignement of text relative to point (x,y), default="l"
			  available values are "l": left, "c" : center, "r" : right
v_align		- vertical alignment of text relative to point (x,y), default="b"
			  available values "t" : top, "m" : middle, "b" : bottom
font_name   - name of font to use, default = Free Sans
font_size   - size of font to use, default = 14
italic      - display text in italic (true/false), default=false
oblique     - display text in oblique (true/false), default=false (I don' see the difference with italic!)
bold        - display text in bold (true/false), default=false
angle       - rotation of text in degrees, default = 0 (horizontal)
colour      - table of colours for text, default = plain white {{1,0xFFFFFF,1}}
			  this table contains one or more tables with format {P,C,A}
              P=position of gradient (0 = beginning of text, 1= end of text)
              C=hexadecimal colour 
              A=alpha (opacity) of color (0=invisible,1=opacity 100%)
              Examples :
              for a plain color {{1,0x00FF00,0.5}}
              for a gradient with two colours {{0,0x00FF00,0.5},{1,0x000033,1}}
              or {{0.5,0x00FF00,1},{1,0x000033,1}} -with this one, gradient will start in the middle of the text
              for a gradient with three colours {{0,0x00FF00,0.5},{0.5,0x000033,1},{1,0x440033,1}}
			  and so on ...
orientation	- in case of gradient, "orientation" defines the starting point of the gradient, default="ww"
			  there are 8 available starting points : "nw","nn","ne","ee","se","ss","sw","ww"
			  (n for north, w for west ...)
			  theses 8 points are the 4 corners + the 4 middles of text's outline
			  so a gradient "nn" will go from "nn" to "ss" (top to bottom, parallele to text)
			  a gradient "nw" will go from "nw" to "se" (left-top corner to right-bottom corner)
radial		- define a radial gradient (if present at the same time as "orientation", "orientation" will have no effect)
			  this parameter is a table with 6 numbers : {xa,ya,ra,xb,yb,rb}
			  they define two circle for the gradient :
			  xa, ya, xb and yb are relative to x and y values above
reflection_alpha    - add a reflection effect (values from 0 to 1) default = 0 = no reflection
                      other values = starting opacity
reflection_scale    - scale of the reflection (default = 1 = height of text)
reflection_length   - length of reflection, define where the opacity will be set to zero
					  calues from 0 to 1, default =1
skew_x,skew_y    - skew text around x or y axis
			  

Needs conky 1.8.0 

To call this script in the conkyrc, in before-TEXT section:
    lua_load /path/to/the/lua/script/text.lua
    lua_draw_hook_pre draw_text
 
v1.0	07/06/2010, Original release
v1.1	10/06/2010	Add "orientation" parameter
v1.2	15/06/2010  Add "h_align", "v_align" and "radial" parameters
v1.3	25/06/2010  Add "reflection_alpha", "reflection_length", "reflection_scale", 
                    "skew_x" et "skew_y"


]]
require 'cairo'

function conky_draw_text()
	--BEGIN OF PARAMETRES
    text_settings={
--SYSTEM LOGO-- ##Arch Linux##
		{
			text="B",
			font_name="OpenLogos",
			font_size=21,
			h_align="l",
			--v_align="m",
			bold=true,
			x=390,
			y=73,
			colour={{0,0Xffffff,0.1},{1,0Xffffff,0.25}},
			--radial={0,300,0,0,300,370},
			orientation="nn",
		},
		{
			text="B",
			font_name="OpenLogos",
			font_size=20,
			h_align="l",
			bold=true,
			orientation="sw",
			x=389.5,
			y=72.5,
			colour={{0,0Xffffff,0.7},{0.5,0Xffffff,0.2}, {1,0Xffffff,0.8}},
		},

}
--------------END OF PARAMETERES----------------
    if conky_window == nil then return end
    if tonumber(conky_parse("$updates"))<3 then return end
       
    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)

    for i,v in pairs(text_settings) do    
        cr = cairo_create (cs)
        display_text(v)
        cairo_destroy(cr)
    end
    
    cairo_surface_destroy(cs)
    


end

function rgb_to_r_g_b2(tcolour)
    colour,alpha=tcolour[2],tcolour[3]
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function display_text(t)

    local function set_pattern()
        --this function set the pattern
        if #t.colour==1 then 
            cairo_set_source_rgba(cr,rgb_to_r_g_b2(t.colour[1]))
        else
            local pat
            
            if t.radial==nil then
                local pts=linear_orientation(t,te)
                pat = cairo_pattern_create_linear (pts[1],pts[2],pts[3],pts[4])
            else
                pat = cairo_pattern_create_radial (t.radial[1],t.radial[2],t.radial[3],t.radial[4],t.radial[5],t.radial[6])
            end
        
            for i=1, #t.colour do
                cairo_pattern_add_color_stop_rgba (pat, t.colour[i][1], rgb_to_r_g_b2(t.colour[i]))
            end
            cairo_set_source (cr, pat)
        end
    end
    
    --set default values if needed
    if t.text==nil then t.text="Conky is good for you !" end
    if t.x==nil then t.x = conky_window.width/2 end
    if t.y==nil then t.y = conky_window.height/2 end
    if t.colour==nil then t.colour={{1,0xFFFFFF,1}} end
    if t.font_name==nil then t.font_name="Free Sans" end
    if t.font_size==nil then t.font_size=14 end
    if t.angle==nil then t.angle=0 end
    if t.italic==nil then t.italic=false end
    if t.oblique==nil then t.oblique=false end
    if t.bold==nil then t.bold=false end
    if t.radial ~= nil then
        if #t.radial~=6 then 
            print ("error in radial table")
            t.radial=nil 
        end
    end
    if t.orientation==nil then t.orientation="ww" end
    if t.h_align==nil then t.h_align="l" end
    if t.v_align==nil then t.v_align="b" end    
    if t.reflection_alpha == nil then t.reflection_alpha=0 end
    if t.reflection_length == nil then t.reflection_length=1 end
    if t.reflection_scale == nil then t.reflection_scale=1 end
    if t.skew_x==nil then t.skew_x=0 end
    if t.skew_y==nil then t.skew_y=0 end    
    cairo_translate(cr,t.x,t.y)
    cairo_rotate(cr,t.angle*math.pi/180)
    cairo_save(cr)       
     
 

    local slant = CAIRO_FONT_SLANT_NORMAL
    local weight =CAIRO_FONT_WEIGHT_NORMAL
    if t.italic then slant = CAIRO_FONT_SLANT_ITALIC end
    if t.oblique then slant = CAIRO_FONT_SLANT_OBLIQUE end
    if t.bold then weight = CAIRO_FONT_WEIGHT_BOLD end
    
    cairo_select_font_face(cr, t.font_name, slant,weight)
 
    for i=1, #t.colour do    
        if #t.colour[i]~=3 then 
            print ("error in color table")
            t.colour[i]={1,0xFFFFFF,1} 
        end
    end

    local matrix0 = cairo_matrix_t:create()
    skew_x,skew_y=t.skew_x/t.font_size,t.skew_y/t.font_size
    cairo_matrix_init (matrix0, 1,skew_y,skew_x,1,0,0)
    cairo_transform(cr,matrix0)
    cairo_set_font_size(cr,t.font_size)
    te=cairo_text_extents_t:create()
    cairo_text_extents (cr,t.text,te)
    
    set_pattern()


            
    mx,my=0,0
    
    if t.h_align=="c" then
        mx=-te.width/2
    elseif t.h_align=="r" then
        mx=-te.width
    end
    if t.v_align=="m" then
        my=-te.height/2-te.y_bearing
    elseif t.v_align=="t" then
        my=-te.y_bearing
    end
    cairo_move_to(cr,mx,my)
    
    cairo_show_text(cr,t.text)

     
        
        
   if t.reflection_alpha ~= 0 then 
        local matrix1 = cairo_matrix_t:create()
        cairo_set_font_size(cr,t.font_size)

        cairo_matrix_init (matrix1,1,0,0,-1*t.reflection_scale,0,(te.height+te.y_bearing+my)*(1+t.reflection_scale))
        cairo_set_font_size(cr,t.font_size)
        te=cairo_text_extents_t:create()
        cairo_text_extents (cr,t.text,te)
        
                
        cairo_transform(cr,matrix1)
        set_pattern()
        cairo_move_to(cr,mx,my)
        cairo_show_text(cr,t.text)

        local pat2 = cairo_pattern_create_linear (0,
                                        (te.y_bearing+te.height+my),
                                        0,
                                        te.y_bearing+my)
        cairo_pattern_add_color_stop_rgba (pat2, 0,1,0,0,1-t.reflection_alpha)
        cairo_pattern_add_color_stop_rgba (pat2, t.reflection_length,0,0,0,1)    
        
        
        cairo_set_line_width(cr,1)
        dy=te.x_bearing
        if dy<0 then dy=dy*(-1) end
        cairo_rectangle(cr,mx+te.x_bearing,te.y_bearing+te.height+my,te.width+dy,-te.height*1.05)
        cairo_clip_preserve(cr)
        cairo_set_operator(cr,CAIRO_OPERATOR_CLEAR)
        --cairo_stroke(cr)
        cairo_mask(cr,pat2)
        cairo_pattern_destroy(pat2)
        cairo_set_operator(cr,CAIRO_OPERATOR_OVER)
    end
    
end


function linear_orientation(t,te)
    local w,h=te.width,te.height
    local xb,yb=te.x_bearing,te.y_bearing
    
    if t.h_align=="c" then
        xb=xb-w/2
    elseif t.h_align=="r" then
        xb=xb-w
       end    
    if t.v_align=="m" then
        yb=-h/2
    elseif t.v_align=="t" then
        yb=0
       end    
       
    if t.orientation=="nn" then
        p={xb+w/2,yb,xb+w/2,yb+h}
    elseif t.orientation=="ne" then
        p={xb+w,yb,xb,yb+h}
    elseif t.orientation=="ww" then
        p={xb,h/2,xb+w,h/2}
    elseif vorientation=="se" then
        p={xb+w,yb+h,xb,yb}
    elseif t.orientation=="ss" then
        p={xb+w/2,yb+h,xb+w/2,yb}
    elseif vorientation=="ee" then
        p={xb+w,h/2,xb,h/2}        
    elseif t.orientation=="sw" then
        p={xb,yb+h,xb+w,yb}
    elseif t.orientation=="nw" then
        p={xb,yb,xb+w,yb+h}
    end
    return p
end
```
vnstat monthly.py:
```
#!/usr/bin/env python2
#
#       vnstat-conky-script.py
#       
#       get monthly download totals from vnstat, for display in conky
#
from subprocess import Popen,PIPE
import sys

def sizeformat(size):
    suffix = ['B','KB','MB','GB','TB']
    count = 0
    while size >= 1024 and count < len(suffix)-1:
        count += 1
        size = size/1024
    return "%.2f%s" % (size, suffix[count])
# get output
output = Popen(["vnstat", "--dumpdb"], stdout= PIPE).communicate()[0]
# get the correct line (first to start with m)
line = (i for i in output.split('\n') if i.startswith('m') ).next()        
#split line out into constituent parts
mon,mon_num,nixtime,rec_mb,tran_mb,rec_kb,tran_kb,inuse=line.split(';')

if sys.argv[1] == '-r': #received
    print sizeformat((float(rec_mb)*1024*1024)+(float(rec_kb)*1024))
elif sys.argv[1] == '-s':#sent
    print sizeformat((float(tran_mb)*1024*1024)+(float(tran_kb)*1024))
else: #return total
    print sizeformat(((float(rec_mb)*1024*1024)+(float(rec_kb)*1024))
        +(float(tran_mb)*1024*1024)+(float(tran_kb)*1024))
```
vinstat daily.py:
```
#!/usr/bin/env python2
#
#       vnstatDAILY-conky-script.py
#       
#       get monthly download totals from vnstat, for display in conky
#
from subprocess import Popen,PIPE
import sys

def sizeformat(size):
    suffix = ['B','KB','MB','GB','TB']
    count = 0
    while size >= 1024 and count < len(suffix)-1:
        count += 1
        size = size/1024
    return "%.2f%s" % (size, suffix[count])
# get output
output = Popen(["vnstat", "--dumpdb"], stdout= PIPE).communicate()[0]
# get the correct line (first to start with m)
line = (i for i in output.split('\n') if i.startswith('d') ).next()        
#split line out into constituent parts
mon,mon_num,nixtime,rec_mb,tran_mb,rec_kb,tran_kb,inuse=line.split(';')

if sys.argv[1] == '-r': #received
    print sizeformat((float(rec_mb)*1024*1024)+(float(rec_kb)*1024))
elif sys.argv[1] == '-s':#sent
    print sizeformat((float(tran_mb)*1024*1024)+(float(tran_kb)*1024))
else: #return total
    print sizeformat(((float(rec_mb)*1024*1024)+(float(rec_kb)*1024))
        +(float(tran_mb)*1024*1024)+(float(tran_kb)*1024))
```
Thats it! :P

---

### Post by Creamy Goodness on 2011-01-03
Hey wlourf,
Sorry, I forgot to check back here recently, busy with the holidays!
I  suspect you are correct about the global vars, I am not sure that they  were causing any memory leaks. It was just something I changed early  while troubleshooting the memory leak, but since it's very hard to gauge  the amount of memory leaking over a short period, I am not even sure it  helped. All I did was watch the percent usage of Conky in Conky, and it  would go up by .01 every 10 seconds or so. Sometimes it would go down  again, maybe as it swapped to the virtual memory, but after another  minute or two it would be even worse. If you do a few searches on google  you can find lots of warnings about the globals in lua not being  garbage collected, and also that they are slow and use more memory, so I  figured I'd better change all of them to local where possible. Anyways  that leak rate was always about the same until I fixed the last missing  pattern destroy, so either it was the worst leak, or ... ? 
Also I am  confused about the lua takeownership function. It seems to be a part of  the tolua source and not conky, conky doc says "you should use  tolua.takeownership() on the return value to ensure ownership is passed  properly". And those cairo_x:create() functions are making memory  structures in conky, so I guess they're saying they won't be destroyed  unless you do what they said. But again, I didn't test this enough to  know if it makes any difference. 
About hosting the scripts online, I  think the best thing to do is upload it to a free source control  repository like gitorius, that way people can review and suggest changes  directly, but I don't see any way to communicate there (like a forum or  mailing list). Code.google.com might be a better all-in-one choice,  they have something called groups available for discussion, good enough  probably.

> **wlourf said:**
> Hi Creamy Goodness,

Thanks for your feedback and your improvments to the scripts.
I started to look to some scripts you have modified, I like the DrawMe  flag and the _to_byte variables and I will add them in futures updates.

I've seen somewhere in a script, that you use :
```
    name="fs_used",
    arg="/",
    max=conky_parse("${to_bytes ${fs_size /}}"),
```but you can find  variables with named with _perc , they give you percentages, like  fs_used_perc, memperc... so you can use this table :
```
            name="fs_used_perc",
            arg="/",
            max=100,
```For the memory leaks (well I have to improve  myself, I agree! the N900 has really 256 MB of memory? ) :
I didn't know "tolua.takeownership()", what does it do exactly ?
I agree : we have to destroy patterns, so I missed somes !

But are you sure that global variables create memory leaks ? When the  conky runs, a global variable is overwritten each time the script is  called, so memory usage should not increase.
And if we use only local variables, I'm not sure to set the variable to "nil" at the end of the script is necessary.

Anyway, local variables are a good practice and I will update the scripts with them and with your ideas soon.

So now, two questions : what is the best tool to see if the memory used by conky is increasing ( top | grep conky ; pmap ?)
I would like to put all my little scripts at the same place so it become  more easy to find them and more easy to modify them for anyone who want  to do it ! Any idea ? I thought of ubuntu PPA but I don't use ubuntu  actually !

Thanks again

---

### Post by maman on 2011-01-05
hello,
```
fg_colour=0xFFFFFF
```It's ok, I haven't seen this, so stupid  :confused:

Thanks a lot wlourf.  
> **wlourf said:**
>  [Don' tell my mother, I'm a conky addict !]("http://u-scripts.blogspot.com/")  Maman knows it, now. :lol: Have fun with your conkys.

See you

---

### Post by wlourf on 2011-01-13
@maman, please don't tell Papa :D

@Creamy Goodness : thanks for the time you take to write the explanations. They were very helpfull and now the memory usage is stable :

text : [http://wlourf.deviantart.com/gallery/#/d36njc0](http://wlourf.deviantart.com/gallery/#/d36njc0)
graph : [http://wlourf.deviantart.com/gallery/#/d31vd5m](http://wlourf.deviantart.com/gallery/#/d31vd5m)
bargraph : [http://wlourf.deviantart.com/gallery/#/d2jj1rz](http://wlourf.deviantart.com/gallery/#/d2jj1rz)
ring : [http://wlourf.deviantart.com/gallery/#/d2vvzqk](http://wlourf.deviantart.com/gallery/#/d2vvzqk)
pie : [http://wlourf.deviantart.com/gallery/#/d2qo9sz](http://wlourf.deviantart.com/gallery/#/d2qo9sz)

Well in fact, the memory used in the ring and in the pie widget grows a little bit but i didn't find where was the leak :( so I will cron a killall conky some times !

---

### Post by wlourf on 2011-01-27
hello again :P

I updated the box widget from previous page.
i add some interesting options (i hope so) on this box : each corner can have its own shape, some composite effects, and a dashed border...
the script is on deviantArt and will be updated on this site :
[http://wlourf.deviantart.com/#/d386bma](http://wlourf.deviantart.com/#/d386bma)

Voilà !

---

### Post by dk75 on 2011-02-09
one, two, three, microphone test...

---

### Post by wlourf on 2011-02-09
hi dk75,
at least, this thread is not dead, like the conky MegaThread ;-)

---

### Post by HOLLYW00D on 2011-02-11
howdy, could someone guide me in adjusting a lua script, of VinDSL's, i found here:

[http://ubuntuforums.org/showpost.php?p=10351826&postcount=15842](http://ubuntuforums.org/showpost.php?p=10351826&postcount=15842)

i added six more CPU readouts in my .conkyrc, which is working fine, but i have no idea of how to modify the lua script and make it all work.

the attached pic is of how conky sits at present.  the two bars under "processors" are supposed to align with cpu's 1 and 2.  the bar that's in between cpu 7 & 8 is actually the "RAM" bar.  i tried to just copy the section referencing the first two cpu's, pasting it a few time and modifying the cpu numbers, but apparently it's not that easy. :)

here's how my lua script sits at present:
```

--[[ BARGRAPH WIDGET
	v2.1 by wlourf (07 Jan. 2011)
	this widget draws a bargraph with different effects 
	http://u-scripts.blogspot.com/2010/07/bargraph-widget.html
	
To call the script in a conky, use, before TEXT
	lua_load /path/to/the/script/bargraph.lua
	lua_draw_hook_pre main_rings
and add one line (blank or not) after TEXT

	
Parameters are :
3 parameters are mandatory
name	- the name of the conky variable to display, for example for {$cpu cpu0}, just write name="cpu"
arg		- the argument of the above variable, for example for {$cpu cpu0}, just write arg="cpu0"
		  arg can be a numerical value if name=""
max		- the maximum value the above variable can reach, for example, for {$cpu cpu0}, just write max=100
	
Optional parameters:
x,y		- coordinates of the starting point of the bar, default = middle of the conky window
cap		- end of cap line, ossibles values are r,b,s (for round, butt, square), default="b"
		  http://www.cairographics.org/samples/set_line_cap/
angle	- angle of rotation of the bar in degress, default = 0 (i.e. a vertical bar)
		  set to 90 for an horizontal bar
skew_x	- skew bar around x axis, default = 0
skew_y	- skew bar around y axis, default = 0
blocks  - number of blocks to display for a bar (values >0) , default= 10
height	- height of a block, default=10 pixels
width	- width of a block, default=20 pixels
space	- space between 2 blocks, default=2 pixels
angle_bar	- this angle is used to draw a bar on a circular way (ok, this is no more a bar !) default=0
radius		- for cicular bars, internal radius, default=0
			  with radius, parameter width has no more effect.

Colours below are defined into braces {colour in hexadecimal, alpha}
fg_colour	- colour of a block ON, default= {0x00FF00,1}
bg_colour	- colour of a block OFF, default = {0x00FF00,0.5}
alarm		- threshold, values after this threshold will use alarm_colour colour , default=max
alarm_colour - colour of a block greater than alarm, default=fg_colour
smooth		- (true or false), create a gradient from fg_colour to bg_colour, default=false 
mid_colour	- colours to add to gradient, with this syntax {position into the gradient (0 to1), colour hexa, alpha}
			  for example, this table {{0.25,0xff0000,1},{0.5,0x00ff00,1},{0.75,0x0000ff,1}} will add
			  3 colurs to gradient created by fg_colour and alarm_colour, default=no mid_colour
led_effect	- add LED effects to each block, default=no led_effect
			  if smooth=true, led_effect is not used
			  possibles values : "r","a","e" for radial, parallelel, perdendicular to the bar (just try!)
			  led_effect has to be used with theses colours :
fg_led		- middle colour of a block ON, default = fg_colour
bg_led		- middle colour of a block OFF, default = bg_colour
alarm_led	- middle colour of a block > ALARM,  default = alarm_colour

reflection parameters, not avaimable for circular bars
reflection_alpha    - add a reflection effect (values from 0 to 1) default = 0 = no reflection
                      other values = starting opacity
reflection_scale    - scale of the reflection (default = 1 = height of text)
reflection_length   - length of reflection, define where the opacity will be set to zero
					  calues from 0 to 1, default =1
reflection			- position of reflection, relative to a vertical bar, default="b"
					  possibles values are : "b","t","l","r" for bottom, top, left, right
draw_me     - if set to false, text is not drawn (default = true or 1)
              it can be used with a conky string, if the string returns 1, the text is drawn :
              example : "${if_empty ${wireless_essid wlan0}}${else}1$endif",

v1.0 (10 Feb. 2010) original release
v1.1 (13 Feb. 2010) numeric values can be passed instead conky stats with parameters name="", arg = numeric_value	
v1.2 (28 Feb. 2010) just renamed the widget to bargraph
v1.3 (03 Mar. 2010) added parameters radius & angle_bar to draw the bar in a circular way
v2.0 (12 Jul. 2010) rewrite script + add reflection effects and parameters are now set into tables
v2.1 (07 Jan. 2011) Add draw_me parameter and correct memory leaks, thanks to "Creamy Goodness"

--      This program is free software; you can redistribute it and/or modify
--      it under the terms of the GNU General Public License as published by
--      the Free Software Foundation version 3 (GPLv3)
--     
--      This program is distributed in the hope that it will be useful,
--      but WITHOUT ANY WARRANTY; without even the implied warranty of
--      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
--      GNU General Public License for more details.
--     
--      You should have received a copy of the GNU General Public License
--      along with this program; if not, write to the Free Software
--      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
--      MA 02110-1301, USA.		

]]

require 'cairo'

----------------START OF PARAMETERS ----------
function conky_main_bars()
	local bars_settings={
		{	--[ Graph for CPU1 ]--
			name="cpu",
			arg="cpu1",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=155,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for CPU2 ]--
			name="cpu",
			arg="cpu2",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=169,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for CPU3 ]--
			name="cpu",
			arg="cpu3",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=155,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for CPU4 ]--
			name="cpu",
			arg="cpu4",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=155,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for CPU5 ]--
			name="cpu",
			arg="cpu5",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=155,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for CPU6 ]--
			name="cpu",
			arg="cpu6",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=169,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for CPU7 ]--
			name="cpu",
			arg="cpu7",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=155,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for CPU8 ]--
			name="cpu",
			arg="cpu8",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=155,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for Memory ]--
			name="memperc",
			arg="",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=218,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for Root ]--
                        name="fs_used_perc",
			arg="/",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=263,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},	
		{	--[ Graph for Home ]--
			name="fs_used_perc",
			arg="/home",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=290,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},	
	        {	--[ Graph for Swap ]--
                        name="swapperc",
			arg="",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=317,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		 }	
	
-----------END OF PARAMETERS--------------


    
	if conky_window == nil then return end
	
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	
	cr = cairo_create(cs)    
	--prevent segmentation error when reading cpu state
    if tonumber(conky_parse('${updates}'))>3 then
        for i in pairs(bars_settings) do
        	
        	draw_multi_bar_graph(bars_settings[i])
        	
        end
    end
	cairo_destroy(cr)
	cairo_surface_destroy(cs)
	cr=nil

end



function draw_multi_bar_graph(t)
	cairo_save(cr)
	--check values
	if t.draw_me == true then t.draw_me = nil end
	if t.draw_me ~= nil and conky_parse(tostring(t.draw_me)) ~= "1" then return end	
	if t.name==nil and t.arg==nil then 
		print ("No input values ... use parameters 'name' with 'arg' or only parameter 'arg' ") 
		return
	end
	if t.max==nil then
		print ("No maximum value defined, use 'max'")
		return
	end
	if t.name==nil then t.name="" end
	if t.arg==nil then t.arg="" end

	--set default values	
	if t.x == nil		then t.x = conky_window.width/2 end
	if t.y == nil		then t.y = conky_window.height/2 end
	if t.blocks == nil	then t.blocks=10 end
	if t.height == nil	then t.height=10 end
	if t.angle == nil 	then t.angle=0 end
	t.angle = t.angle*math.pi/180
	--line cap style
	if t.cap==nil		then t.cap = "b" end
	local cap="b"
	for i,v in ipairs({"s","r","b"}) do 
		if v==t.cap then cap=v end
	end
	local delta=0
	if t.cap=="r" or t.cap=="s" then delta = t.height end
	if cap=="s" then 	cap = CAIRO_LINE_CAP_SQUARE
	elseif cap=="r" then
		cap = CAIRO_LINE_CAP_ROUND
	elseif cap=="b" then
		cap = CAIRO_LINE_CAP_BUTT
	end
	--end line cap style
	--if t.led_effect == nil	then t.led_effect="r" end
	if t.width == nil	then t.width=20 end
	if t.space == nil	then t.space=2 end
	if t.radius == nil	then t.radius=0 end
	if t.angle_bar == nil	then t.angle_bar=0 end
	t.angle_bar = t.angle_bar*math.pi/360 --halt angle
	
	--colours
	if t.bg_colour == nil 	then t.bg_colour = {0x00FF00,0.5} end
	if #t.bg_colour~=2 		then t.bg_colour = {0x00FF00,0.5} end
	if t.fg_colour == nil 	then t.fg_colour = {0x00FF00,1} end
	if #t.fg_colour~=2 		then t.fg_colour = {0x00FF00,1} end
	if t.alarm_colour == nil 	then t.alarm_colour = t.fg_colour end
	if #t.alarm_colour~=2 		then t.alarm_colour = t.fg_colour end

	if t.mid_colour ~= nil then	
		for i=1, #t.mid_colour do    
		    if #t.mid_colour[i]~=3 then 
		    	print ("error in mid_color table")
		    	t.mid_colour[i]={1,0xFFFFFF,1} 
		    end
		end
    end
    
	if t.bg_led ~= nil and #t.bg_led~=2	then t.bg_led = t.bg_colour end
	if t.fg_led ~= nil and #t.fg_led~=2	then t.fg_led = t.fg_colour end
	if t.alarm_led~= nil and #t.alarm_led~=2 then t.alarm_led = t.fg_led end
	
	if t.led_effect~=nil then
		if t.bg_led == nil then t.bg_led = t.bg_colour end
		if t.fg_led == nil 	then t.fg_led = t.fg_colour end
		if t.alarm_led == nil  then t.alarm_led = t.fg_led end
	end
	

	if t.alarm==nil then t.alarm = t.max end --0.8*t.max end
	if t.smooth == nil then t.smooth = false end

	if t.skew_x == nil then 
		t.skew_x=0 
	else
		t.skew_x = math.pi*t.skew_x/180	
	end
	if t.skew_y == nil then 
		t.skew_y=0
	else
		t.skew_y = math.pi*t.skew_y/180	
	end
	
	if t.reflection_alpha==nil then t.reflection_alpha=0 end
	if t.reflection_length==nil then t.reflection_length=1 end
	if t.reflection_scale==nil then t.reflection_scale=1 end
	
	--end of default values
	

 	local function rgb_to_r_g_b(col_a)
		return ((col_a[1] / 0x10000) % 0x100) / 255., ((col_a[1] / 0x100) % 0x100) / 255., (col_a[1] % 0x100) / 255., col_a[2]
	end
	
	
	--functions used to create patterns

	local function create_smooth_linear_gradient(x0,y0,x1,y1)
		local pat = cairo_pattern_create_linear (x0,y0,x1,y1)
		cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
		cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
		if t.mid_colour ~=nil then
			for i=1, #t.mid_colour do
				cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
			end
		end
		return pat
	end

	local function create_smooth_radial_gradient(x0,y0,r0,x1,y1,r1)
		local pat =  cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
		cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
		cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
		if t.mid_colour ~=nil then
			for i=1, #t.mid_colour do
				cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
			end
		end
		return pat
	end
	
	local function create_led_linear_gradient(x0,y0,x1,y1,col_alp,col_led)
		local pat = cairo_pattern_create_linear (x0,y0,x1,y1) ---delta, 0,delta+ t.width,0)
		cairo_pattern_add_color_stop_rgba (pat, 0.0, rgb_to_r_g_b(col_alp))
		cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
		cairo_pattern_add_color_stop_rgba (pat, 1.0, rgb_to_r_g_b(col_alp))
		return pat
	end

	local function create_led_radial_gradient(x0,y0,r0,x1,y1,r1,col_alp,col_led,mode)
		local pat = cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
		if mode==3 then
			cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_alp))				
			cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
			cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))				
		else
			cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_led))
			cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))				
		end
		return pat
	end






	local function draw_single_bar()
		--this fucntion is used for bars with a single block (blocks=1) but 
		--the drawing is cut in 3 blocks : value/alarm/background
		--not zvzimzblr for circular bar
		local function create_pattern(col_alp,col_led,bg)
			local pat
			
			if not t.smooth then
				if t.led_effect=="e" then
					pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
				elseif t.led_effect=="a" then
					pat = create_led_linear_gradient (t.width/2, 0,t.width/2,-t.height,col_alp,col_led)
				elseif  t.led_effect=="r" then
					pat = create_led_radial_gradient (t.width/2, -t.height/2, 0, t.width/2,-t.height/2,t.height/1.5,col_alp,col_led,2)
				else
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
				end
			else
				if bg then
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
				else
					pat = create_smooth_linear_gradient(t.width/2, 0, t.width/2,-t.height)
				end
			end
			return pat
		end
		
		local y1=-t.height*pct/100
		local y2,y3
		if pct>(100*t.alarm/t.max) then 
			y1 = -t.height*t.alarm/100
			y2 = -t.height*pct/100
			if t.smooth then y1=y2 end
		end
		
		if t.angle_bar==0 then
		
			--block for fg value
			local pat = create_pattern(t.fg_colour,t.fg_led,false)
			cairo_set_source(cr,pat)
			cairo_rectangle(cr,0,0,t.width,y1)
			cairo_fill(cr)
			cairo_pattern_destroy(pat)
		
			-- block for alarm value			
			if not t.smooth and y2 ~=nil then 
				pat = create_pattern(t.alarm_colour,t.alarm_led,false)
				cairo_set_source(cr,pat)
				cairo_rectangle(cr,0,y1,t.width,y2-y1)
				cairo_fill(cr)
				y3=y2
				cairo_pattern_destroy(pat)
			else
				y2,y3=y1,y1
			end
			-- block for bg value
			cairo_rectangle(cr,0,y2,t.width,-t.height-y3)
			pat = create_pattern(t.bg_colour,t.bg_led,true)
			cairo_set_source(cr,pat)
			cairo_pattern_destroy(pat)
			cairo_fill(cr)
		end		
	end  --end single bar
	





	local function draw_multi_bar()
		--function used for bars with 2 or more blocks
		for pt = 1,t.blocks do 
			--set block y
			local y1 = -(pt-1)*(t.height+t.space)
			local light_on=false
			
			--set colors
			local col_alp = t.bg_colour
			local col_led = t.bg_led
			if pct>=(100/t.blocks) or pct>0 then --ligth on or not the block
				if pct>=(pcb*(pt-1))  then 
					light_on = true
					col_alp = t.fg_colour
					col_led = t.fg_led
					if pct>=(100*t.alarm/t.max) and (pcb*pt)>(100*t.alarm/t.max) then 
						col_alp = t.alarm_colour 
						col_led = t.alarm_led 
					end
				end
			end

			--set colors
			--have to try to create gradients outside the loop ?
			local pat 
			
			if not t.smooth then
				if t.angle_bar==0 then
					if t.led_effect=="e" then
						pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
					elseif t.led_effect=="a" then
						pat = create_led_linear_gradient (t.width/2, -t.height/2+y1,t.width/2,0+t.height/2+y1,col_alp,col_led)					
					elseif  t.led_effect=="r" then
						pat = create_led_radial_gradient (t.width/2, y1, 0, t.width/2,y1,t.width/1.5,col_alp,col_led,2)	
					else
						pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
					end
				else
					 if t.led_effect=="a"  then
						 pat = create_led_radial_gradient (0, 0, t.radius+(t.height+t.space)*(pt-1),
														 0, 0, t.radius+(t.height+t.space)*(pt),						 
											 col_alp,col_led,3)	
					else
						pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))					
					end
					
				end
			else
				
				if light_on then
					if t.angle_bar==0 then
						pat = create_smooth_linear_gradient(t.width/2, t.height/2, t.width/2,-(t.blocks-0.5)*(t.height+t.space))
					else
						pat = create_smooth_radial_gradient(0, 0, (t.height+t.space),  0,0,(t.blocks+1)*(t.height+t.space),2)
					end
				else		
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
				end
			end
			cairo_set_source (cr, pat)
			cairo_pattern_destroy(pat)

			--draw a block
			if t.angle_bar==0 then
				cairo_move_to(cr,0,y1)
				cairo_line_to(cr,t.width,y1)
			else		
				cairo_arc( cr,0,0,
					t.radius+(t.height+t.space)*(pt)-t.height/2,
					 -t.angle_bar -math.pi/2 ,
					 t.angle_bar -math.pi/2)
			end
			cairo_stroke(cr)
		end	
	end
	
	
	
	
	local function setup_bar_graph()
		--function used to retrieve the value to display and to set the cairo structure
		if t.blocks ~=1 then t.y=t.y-t.height/2 end
		
		local value = 0
		if t.name ~="" then
			value = tonumber(conky_parse(string.format('${%s %s}', t.name, t.arg)))
			--$to_bytes doesn't work when value has a decimal point,
			--https://garage.maemo.org/plugins/ggit/browse.php/?p=monky;a=commitdiff;h=174c256c81a027a2ea406f5f37dc036fac0a524b;hp=d75e2db5ed3fc788fb8514121f67316ac3e5f29f
			--http://sourceforge.net/tracker/index.php?func=detail&aid=3000865&group_id=143975&atid=757310
			--conky bug?
			--value = (conky_parse(string.format('${%s %s}', t.name, t.arg)))
			--if string.match(value,"%w") then
			--	value = conky_parse(string.format('${to_bytes %s}',value))
			--end
		else
			value = tonumber(t.arg)
		end

		if value==nil then value =0 end
		
		pct = 100*value/t.max
		pcb = 100/t.blocks
		
		cairo_set_line_width (cr, t.height)
		cairo_set_line_cap  (cr, cap)
		cairo_translate(cr,t.x,t.y)
		cairo_rotate(cr,t.angle)

		local matrix0 = cairo_matrix_t:create()
		tolua.takeownership(matrix0)
		cairo_matrix_init (matrix0, 1,t.skew_y,t.skew_x,1,0,0)
		cairo_transform(cr,matrix0)

	
		
		--call the drawing function for blocks
		if t.blocks==1 and t.angle_bar==0 then
			draw_single_bar()
			if t.reflection=="t" or t.reflection=="b" then cairo_translate(cr,0,-t.height) end
		else
			draw_multi_bar()
		end

		--dot for reminder
		--[[
		if t.blocks ~=1 then
			cairo_set_source_rgba(cr,1,0,0,1)
			cairo_arc(cr,0,t.height/2,3,0,2*math.pi)
			cairo_fill(cr)
		else
			cairo_set_source_rgba(cr,1,0,0,1)
			cairo_arc(cr,0,0,3,0,2*math.pi)
			cairo_fill(cr)
		end]]
		
		--call the drawing function for reflection and prepare the mask used		
		if t.reflection_alpha>0 and t.angle_bar==0 then
			local pat2
			local matrix1 = cairo_matrix_t:create()
			tolua.takeownership(matrix1)
			if t.angle_bar==0 then
				pts={-delta/2,(t.height+t.space)/2,t.width+delta,-(t.height+t.space)*(t.blocks)}
				if t.reflection=="t" then
					cairo_matrix_init (matrix1,1,0,0,-t.reflection_scale,0,-(t.height+t.space)*(t.blocks-0.5)*2*(t.reflection_scale+1)/2)
					pat2 = cairo_pattern_create_linear (t.width/2,-(t.height+t.space)*(t.blocks),t.width/2,(t.height+t.space)/2)
				elseif t.reflection=="r" then
					cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,delta+2*t.width,0)
					pat2 = cairo_pattern_create_linear (delta/2+t.width,0,-delta/2,0)
				elseif t.reflection=="l" then
					cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,-delta,0)
					pat2 = cairo_pattern_create_linear (-delta/2,0,delta/2+t.width,-0)
				else --bottom
					cairo_matrix_init (matrix1,1,0,0,-1*t.reflection_scale,0,(t.height+t.space)*(t.reflection_scale+1)/2)
					pat2 = cairo_pattern_create_linear (t.width/2,(t.height+t.space)/2,t.width/2,-(t.height+t.space)*(t.blocks))
				end
			end
			cairo_transform(cr,matrix1)

			if t.blocks==1 and t.angle_bar==0 then
				draw_single_bar()
				cairo_translate(cr,0,-t.height/2) 
			else
				draw_multi_bar()
			end
			
			
			cairo_set_line_width(cr,0.01)
			cairo_pattern_add_color_stop_rgba (pat2, 0,0,0,0,1-t.reflection_alpha)
			cairo_pattern_add_color_stop_rgba (pat2, t.reflection_length,0,0,0,1)
			if t.angle_bar==0 then
				cairo_rectangle(cr,pts[1],pts[2],pts[3],pts[4])
			end
			cairo_clip_preserve(cr)
			cairo_set_operator(cr,CAIRO_OPERATOR_CLEAR)
			cairo_stroke(cr)
			cairo_mask(cr,pat2)
			cairo_pattern_destroy(pat2)
			cairo_set_operator(cr,CAIRO_OPERATOR_OVER)
			
		end --reflection
		pct,pcb=nil
	end --setup_bar_graph()
	
	--start here !
	setup_bar_graph()
	cairo_restore(cr)
end

```

any help would be greatly appreciated.


***EDIT***
standby, i think i figured it out.  copy and paste....  now i need to adjust the X and Y.  d'oh!  =)

---

### Post by mrpeachy on 2011-03-10
good evening

i am running an external command in lua using the io.popen command

but the external command takes longer to execute (im calling curl) than the conky update interval (1 second)

the result is that the lua script hangs until the command has finished

is there any way to have the lua script continue to run and execute the command without hanging?

thanks :D

or should i just not be doing things like curl via lua io.popen??

assuming anyone still reads this thread :)

---

### Post by dk75 on 2011-03-15
Easiest way is to run CURL thing in CRONTAB with BASH or Python and to parse result with LUA only.
But maybe it is a way to do threading in Conky-LUA.
Need a research.
[edit]
.
..
...
[http://lua-users.org/wiki/ThreadsTutorial](http://lua-users.org/wiki/ThreadsTutorial) - I don't understand it completely, except for "don't use threads" ;P

Coroutines (didn't tested it yet): [http://www.lua.org/pil/9.html](http://www.lua.org/pil/9.html)

Coroutines:
[http://www.lua.org/manual/5.0/manual.html#2.10](http://www.lua.org/manual/5.0/manual.html#2.10)
[http://www.lua.org/manual/5.0/manual.html#5.2](http://www.lua.org/manual/5.0/manual.html#5.2)
Threads:
[http://www.lua.org/manual/5.0/manual.html#3.20](http://www.lua.org/manual/5.0/manual.html#3.20)

Check it out.

---

### Post by mrpeachy on 2011-03-15
thanks dk75

i found this page about coroutines
[http://lua-users.org/wiki/CoroutinesTutorial](http://lua-users.org/wiki/CoroutinesTutorial)

but i haven't been able to get it to work

perhaps it the way that conky runs the lua script
ie effectively restarting the script every conky cycle (at least that's how i understand it)
which is preventing the coroutine to run alongside the main function.

i hope you give it a go and can get it working :D

but for now i thinkim going to curl with bash to a temporary text file then read the file with lua and edit (oening a text file doesn't seem to cause any delays)

---

### Post by Clicksights on 2011-03-21
I have a problem in conky. or better said the .lua with the wireless_bitrate not showing up in my rings.
i now the wireless_bitrate works, as it shows the result in my conky but those are numbers, not rings..
The ring just wont work.

I took out the following code, than conky works OK.
So the mistake must be in there... only i can find one....
Do i try something thats not possible?
This is the part of my .lua config that gives the trouble:

```
{
        name='wireless_bitrate',
        arg='wlan0',
        max=300,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=150, y=500,
        radius=20,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
```i googled but couldn't find an answer.
Hope some one can help me outbeen trying for hours without result.
Help is much appreciated!

PS. this is the message i got:
```
function conky_clock_rings execution failed: /home/user/.lua/scripts/clock_rings.lua:356: attempt to perform arithmetic on local 'value' (a nil value)
```

---

### Post by wlourf on 2011-03-23
> **Clicksights said:**
> I have a problem in conky. or better said the .lua with the wireless_bitrate not showing up in my rings.
i now the wireless_bitrate works, as it shows the result in my conky but those are numbers, not rings..
The ring just wont work.

Hi,

 It's because $wireless_bitrate returns a value WITH an unit (for example 54 Mb/s) and the script is expected a number value.
But you can remove the unit in Lua, for example :
```
{
        name='',
        arg=conky_parse("${wireless_bitrate wlan0}"):gsub(" Mb/s",""),
        max=300,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=150, y=500,
        radius=20,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
```If this doesn't work, post your full script and what $wireless_bitrate returns in a conky !

---

### Post by Clicksights on 2011-03-23
Thanks, now i understand what i missed!
sadly though, no solution yet....

i tried your solution :-( didn't work out...
conky does appear but not the ring showing the wifi speed...
and i got some errors again.

here is my full .LUA

```
--[[
Clock Rings by Linux Mint (2011) reEdited by despot77

This script draws percentage meters as rings, and also draws clock hands if you want! It is fully customisable; all options are described in the script. This script is based off a combination of my clock.lua script and my rings.lua script.

IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.

To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/clock_rings.lua
    lua_draw_hook_pre clock_rings
    
Changelog:
+ v1.0 -- Original release (30.09.2009)
   v1.1p -- Jpope edit londonali1010 (05.10.2009)
*v 2011mint -- reEdit despot77 (18.02.2011)
]]

settings_table = {
    {
        -- Edit this table to customise your rings.
        -- You can create more rings simply by adding more elements to settings_table.
        -- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
        name='time',
        -- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
        arg='%I.%M',
        -- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
        max=12,
        -- "bg_colour" is the colour of the base ring.
        bg_colour=0xffffff,
        -- "bg_alpha" is the alpha value of the base ring.
        bg_alpha=0.1,
        -- "fg_colour" is the colour of the indicator part of the ring.
        fg_colour=0xFF6600,
        -- "fg_alpha" is the alpha value of the indicator part of the ring.
        fg_alpha=0.2,
        -- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
        x=100, y=150,
        -- "radius" is the radius of the ring.
        radius=50,
        -- "thickness" is the thickness of the ring, centred around the radius.
        thickness=5,
        -- "start_angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
        start_angle=0,
        -- "end_angle" is the ending angle of the ring, in degrees, clockwise from top. Value can be either positive or negative, but must be larger than start_angle.
        end_angle=360
    },
    {
        name='time',
        arg='%M.%S',
        max=60,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xFF6600,
        fg_alpha=0.4,
        x=100, y=150,
        radius=56,
        thickness=5,
        start_angle=0,
        end_angle=360
    },
    {
        name='time',
        arg='%S',
        max=60,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xFF6600,
        fg_alpha=0.6,
        x=100, y=150,
        radius=62,
        thickness=5,
        start_angle=0,
        end_angle=360
    },
    {
        name='time',
        arg='%d',
        max=31,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=100, y=150,
        radius=70,
        thickness=5,
        start_angle=-90,
        end_angle=90
    },
    {
        name='time',
        arg='%m',
        max=12,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xFF6600,
        fg_alpha=1,
        x=100, y=150,
        radius=76,
        thickness=5,
        start_angle=-90,
        end_angle=90
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xff6600,
        fg_alpha=0.8,
        x=50, y=300,
        radius=25,
        thickness=5,
        start_angle=-90,
        end_angle=180
    },
{
        name='freq_g',
        arg='1',
        max=2,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xff6600,
        fg_alpha=0.8,
        x=75, y=350,
        radius=25,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
       {
        name='freq_g',
        arg='2',
        max=2,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xff6600,
        fg_alpha=0.8,
        x=75, y=350,
        radius=20,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
    {
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=100, y=400,
        radius=25,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
    {
        name='cpu',
        arg='cpu2',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=100, y=400,
        radius=20,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
{
        name='fs_used_perc',
        arg='/',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=125, y=450,
        radius=25,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
 {
        name='fs_used_perc',
        arg='/home',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=125, y=450,
        radius=20,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
        {
        name='wireless_link_qual',
        arg='wlan0',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=150, y=500,
        radius=25,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
[COLOR=Red] --{
 --      name='wireless_bitrate',
 --      arg='wlan0',
 --      max=300,
 --      bg_colour=0xffffff,
 --      bg_alpha=0.2,
 --      fg_colour=0xFF6600,
 --      fg_alpha=0.8,
 --      x=150, y=500,
 --      radius=20,
 --      thickness=4,
 --      start_angle=-90,
 --      end_angle=180
 --  },[/COLOR]
        {
        name='acpitemp',
        arg='',
        max=75,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=175, y=550,
        radius=25,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
{
        name='execpi 300 hddtemp /dev/sda',
        arg='-n',
        max=75,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=175, y=550,
        radius=20,
        thickness=4,
        start_angle=-90,
        end_angle=180
    },
}

-- Use these settings to define the origin and extent of your clock.

clock_r=65

-- "clock_x" and "clock_y" are the coordinates of the centre of the clock, in pixels, from the top left of the Conky window.

clock_x=100
clock_y=150

show_seconds=true

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(cr,t,pt)
    local w,h=conky_window.width,conky_window.height
    
    local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

    local angle_0=sa*(2*math.pi/360)-math.pi/2
    local angle_f=ea*(2*math.pi/360)-math.pi/2
    local t_arc=t*(angle_f-angle_0)

    -- Draw background ring

    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
    
    -- Draw indicator ring

    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
end

function draw_clock_hands(cr,xc,yc)
    local secs,mins,hours,secs_arc,mins_arc,hours_arc
    local xh,yh,xm,ym,xs,ys
    
    secs=os.date("%S")    
    mins=os.date("%M")
    hours=os.date("%I")
        
    secs_arc=(2*math.pi/60)*secs
    mins_arc=(2*math.pi/60)*mins+secs_arc/60
    hours_arc=(2*math.pi/12)*hours+mins_arc/12
        
    -- Draw hour hand
    
    xh=xc+0.7*clock_r*math.sin(hours_arc)
    yh=yc-0.7*clock_r*math.cos(hours_arc)
    cairo_move_to(cr,xc,yc)
    cairo_line_to(cr,xh,yh)
    
    cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
    cairo_set_line_width(cr,5)
    cairo_set_source_rgba(cr,1.0,1.0,1.0,1.0)
    cairo_stroke(cr)
    
    -- Draw minute hand
    
    xm=xc+clock_r*math.sin(mins_arc)
    ym=yc-clock_r*math.cos(mins_arc)
    cairo_move_to(cr,xc,yc)
    cairo_line_to(cr,xm,ym)
    
    cairo_set_line_width(cr,3)
    cairo_stroke(cr)
    
    -- Draw seconds hand
    
    if show_seconds then
        xs=xc+clock_r*math.sin(secs_arc)
        ys=yc-clock_r*math.cos(secs_arc)
        cairo_move_to(cr,xc,yc)
        cairo_line_to(cr,xs,ys)
    
        cairo_set_line_width(cr,1)
        cairo_stroke(cr)
    end
end

function conky_clock_rings()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
        
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
        
        value=tonumber(str)
        pct=value/pt['max']
        
        draw_ring(cr,pct,pt)
    end
    
    -- Check that Conky has been running for at least 5s

    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    
    local cr=cairo_create(cs)    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
    end
    
    draw_clock_hands(cr,clock_x,clock_y)
end
```i blanked out ( -- ) the part that gives me trouble... :(
it works as it is,but i do want that ring to work....

here is the cronkyrc :

```
# Conky settings #
background yes
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0

temperature_unit fahrenheit

# Window specifications #

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5

uppercase no

temperature_unit celsius


default_color FFFFFF

# Lua Load  #
lua_load ~/.lua/scripts/clock_rings.lua
lua_draw_hook_pre clock_rings

TEXT
${voffset 8}${color FF6600}${font caviar dreams:size=16}${time %A}${font}${voffset -8}${alignr 50}${color FFFFFF}${font caviar dreams:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color FFFFFF}${font caviar dreams:size=18}${time %b}${font}${voffset -3} ${color FFFFFF}${font caviar dreams:size=20}${time %Y}${font}${color FF6600}${hr}
${voffset 140}${font caviar dreams:size=10}${alignr}HOME${font}
${font caviar dreams:size=12}${color FFFFFF}${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EHDL temperature temperature 30} °C${font}
${image ~/.conky/new-ubuntu-logo.png -p 64,125 -s 70x20}
# RINGS #
${color FFFFFF}${goto 22}${voffset 47}${memperc}%
${color FF6600}${goto 22}RAM
${color FFFFFF}${goto 47}${voffset 24}${freq_g (2)}
${color FFFFFF}${goto 47}${freq_g (1)}
${color FF6600}${goto 47}CPU
${color FFFFFF}${goto 72}${voffset 11}${cpu cpu2}%
${color FFFFFF}${goto 72}${cpu cpu1}%
${color FF6600}${goto 72}Load
${color FFFFFF}${goto 97}${voffset 11}${fs_used_perc /home}%
${color FFFFFF}${goto 97}${fs_used_perc /}%
${color FF6600}${goto 97}Disk
${color FFFFFF}${goto 121}${voffset 11}${wireless_bitrate wlan0}
${color FFFFFF}${goto 121}${wireless_link_qual wlan0}%
${color FF6600}${goto 121}Wifi
${color FFFFFF}${goto 145}${voffset 12}${execpi 300 hddtemp /dev/sda -n}°C
${color FFFFFF}${goto 145}${acpitemp}°C 
${color FF6600}${goto 145}Temp


# NET #

${downspeedgraph 30,100 666666 666666}${voffset -79}
${color FF6600}${font caviar dreams:size=10}NET
${if_up wlan0}${color FFFFFF}${font caviar dreams:size=8}eSSID:  ${wireless_essid wlan0}${endif}
${if_up eth0}${color FFFFFF}${font caviar dreams:size=8}AP:        $gw_ip ${endif}
${if_up wlan0}${color FFFFFF}${font caviar dreams:size=8}Wlan:   ${addr wlan0}${endif}
${if_up eth0}${color FFFFFF}${font caviar dreams:size=8}Eth:      ${addr eth0} ${endif}
${color FFFFFF}${font caviar dreams:size=8}Open ports: ${tcp_portmon 1 65535 count}
${color FFFFFF}${font caviar dreams:size=8}IP: ${alignr}DPORT
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  0}${alignr 1}${tcp_portmon 1 65535 rport  0}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  1}${alignr 1}${tcp_portmon 1 65535 rport  1}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  2}${alignr 1}${tcp_portmon 1 65535 rport  2}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  3}${alignr 1}${tcp_portmon 1 65535 rport  3}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  4}${alignr 1}${tcp_portmon 1 65535 rport  4}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  5}${alignr 1}${tcp_portmon 1 65535 rport  5}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  6}${alignr 1}${tcp_portmon 1 65535 rport  6}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  7}${alignr 1}${tcp_portmon 1 65535 rport  7}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  8}${alignr 1}${tcp_portmon 1 65535 rport  8}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  9}${alignr 1}${tcp_portmon 1 65535 rport  9}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 10}${alignr 1}${tcp_portmon 1 65535 rport 10}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 11}${alignr 1}${tcp_portmon 1 65535 rport 11}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 12}${alignr 1}${tcp_portmon 1 65535 rport 12}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 13}${alignr 1}${tcp_portmon 1 65535 rport 13}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 14}${alignr 1}${tcp_portmon 1 65535 rport 14}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 15}${alignr 1}${tcp_portmon 1 65535 rport 15}
# SYSTEM #

${color FF6600}${font caviar dreams:size=8}${alignr}${nodename}
${color FF6600}${font caviar dreams:size=8}${alignr}${pre_exec cat /etc/issue.net}  $machine
${color FF6600}${font caviar dreams:size=8}${alignr}Kernel: ${kernel}
${color FF6600}${font caviar dreams:size=8}${alignr}Uptime: ${uptime_short}
${color FF6600}${font caviar dreams:size=8}${alignr}Processes: ${processes}
${color FF6600}${font caviar dreams:size=8}${alignr}Running: ${running_processes}
${color FF6600}${font OpenLogos:size=19}${voffset -76}u${font}
```

I mixed up some conkys and made this, hope you like it, dont use it on white or black background!
it won't show up good. Please try and feel free to comment and solve my problem! :)
put the lua file in home/.lua/scripts/ !
i use it with this wallpaper in ubuntu netbook: 

```
http://technology.desktopnexus.com/get/38807
```
It looks so damn nice on my netbook.... i love it...

hope you can help! :o

---

### Post by Clicksights on 2011-03-24
hi again,

did some more work to my conky,
still have the same problem though...
so 1st question stays.....

i finally got only the active wifi/lan adaptor ip address showing up when active, and not showing when not connected!
:-P
so happy again!

but it gives a new problem...
Now the data (temp) in conky, those are just beneath the wifi rings, go up a bit when there is no data for the wifi speed...
:-(
so my 2nd question would be, is it possible to use the stripping of the mp/s in the conkyrc file?
So i can leave a static text with mps, and thus avoid the Temp data moving up, when there is no connection on wlan?
:-) i want to have it staying at the same place. it took a long time to get everything right!

also i noticed that if i disconnect from my wlan, the ring stays at the last signal strength....
It doesn't drop to zero. Wonder how to solve that one too...
It does go back when i restart conky manually.

O, and i added external ip! works like a charm!
It does make me wonder if i can also show my ap external ip and ap internal ip ONLY if there is a connection....
maybe  i can put 2 arguments in 1 line,

```
${if_existing /sys/class/net/eth0/operstate up}
```and 

```
${if_existing /sys/class/net/wlan0/operstate up}
```and merge them before the 

```
$gw_ip
```Does some-one now this? or is there another way, like the:

```
${if_existing /sys/class/net/wlan0/operstate up}
```method? Is there such a file for the AP?

To be clear, the moving wifi/temp problem is in this file, and the wifi speed ring is still not working!
Here is my new conky with active wifi/net and external ip showing! :-)
Lua same as before.

```
# Conky settings #
background yes
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0

temperature_unit fahrenheit

# Window specifications #

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5

uppercase no

temperature_unit celsius


default_color FFFFFF

# Lua Load  #
lua_load ~/.lua/scripts/clock_rings.lua
lua_draw_hook_pre clock_rings

TEXT
${voffset 8}${color FF6600}${font caviar dreams:size=16}${time %A}${font}${voffset -8}${alignr 50}${color FFFFFF}${font caviar dreams:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color FFFFFF}${font caviar dreams:size=18}${time %b}${font}${voffset -3} ${color FFFFFF}${font caviar dreams:size=20}${time %Y}${font}${color FF6600}${hr}
${voffset 140}${font caviar dreams:size=10}${alignr}HOME${font}
${font caviar dreams:size=12}${color FFFFFF}${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EHDL temperature temperature 30} °C${font}
${image ~/.conky/new-ubuntu-logo.png -p 64,125 -s 70x20}
# RINGS #
${color FFFFFF}${goto 22}${voffset 47}${memperc}%
${color FF6600}${goto 22}RAM
${color FFFFFF}${goto 47}${voffset 24}${freq_g (2)}
${color FFFFFF}${goto 47}${freq_g (1)}
${color FF6600}${goto 47}CPU
${color FFFFFF}${goto 72}${voffset 11}${cpu cpu2}%
${color FFFFFF}${goto 72}${cpu cpu1}%
${color FF6600}${goto 72}Load
${color FFFFFF}${goto 97}${voffset 11}${fs_used_perc /home}%
${color FFFFFF}${goto 97}${fs_used_perc /}%
${color FF6600}${goto 97}Disk
${color FFFFFF}${goto 121}${voffset 11}${if_existing /sys/class/net/wlan0/operstate up}${wireless_bitrate wlan0}
${color FFFFFF}${goto 121}${wireless_link_qual wlan0}${endif}%
${color FF6600}${goto 121}Wifi
${color FFFFFF}${goto 145}${voffset 12}${execpi 300 hddtemp /dev/sda -n}°C
${color FFFFFF}${goto 145}${acpitemp}°C 
${color FF6600}${goto 145}Temp


# NET #

${downspeedgraph 30,100 666666 666666}${voffset -92}
${color FF6600}${font caviar dreams:size=10}NET
${if_existing /sys/class/net/wlan0/operstate up}${color FFFFFF}${font caviar dreams:size=8}eSSID:  ${wireless_essid wlan0}${endif}
${color FFFFFF}${font caviar dreams:size=8}AP IP:    ${texeci 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${color FFFFFF}${font caviar dreams:size=8}AP:        $gw_ip
${if_existing /sys/class/net/wlan0/operstate up}${color FFFFFF}${font caviar dreams:size=8}Wlan:   ${addr wlan0}${endif}
${if_existing /sys/class/net/eth0/operstate up}${color FFFFFF}${font caviar dreams:size=8}Eth:      ${addr eth0} ${endif}
${color FFFFFF}${font caviar dreams:size=8}Open ports: ${tcp_portmon 1 65535 count}
${color FFFFFF}${font caviar dreams:size=8}IP: ${alignr}DPORT
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  0}${alignr 1}${tcp_portmon 1 65535 rport  0}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  1}${alignr 1}${tcp_portmon 1 65535 rport  1}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  2}${alignr 1}${tcp_portmon 1 65535 rport  2}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  3}${alignr 1}${tcp_portmon 1 65535 rport  3}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  4}${alignr 1}${tcp_portmon 1 65535 rport  4}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  5}${alignr 1}${tcp_portmon 1 65535 rport  5}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  6}${alignr 1}${tcp_portmon 1 65535 rport  6}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  7}${alignr 1}${tcp_portmon 1 65535 rport  7}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  8}${alignr 1}${tcp_portmon 1 65535 rport  8}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip  9}${alignr 1}${tcp_portmon 1 65535 rport  9}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 10}${alignr 1}${tcp_portmon 1 65535 rport 10}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 11}${alignr 1}${tcp_portmon 1 65535 rport 11}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 12}${alignr 1}${tcp_portmon 1 65535 rport 12}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 13}${alignr 1}${tcp_portmon 1 65535 rport 13}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 14}${alignr 1}${tcp_portmon 1 65535 rport 14}
${color FFFFFF}${font caviar dreams:size=8}${tcp_portmon 1 65535 rip 15}${alignr 1}${tcp_portmon 1 65535 rport 15}
# SYSTEM #

${color FF6600}${font caviar dreams:size=8}${alignr}${nodename}
${color FF6600}${font caviar dreams:size=8}${alignr}${pre_exec cat /etc/issue.net}  $machine
${color FF6600}${font caviar dreams:size=8}${alignr}Kernel: ${kernel}
${color FF6600}${font caviar dreams:size=8}${alignr}Uptime: ${uptime_short}
${color FF6600}${font caviar dreams:size=8}${alignr}Processes: ${processes}
${color FF6600}${font caviar dreams:size=8}${alignr}Running: ${running_processes}
${color FF6600}${font OpenLogos:size=19}${voffset -76}u${font}

```

---

### Post by wlourf on 2011-03-28
Clicksight,

Please, post the return of  ${wireless_bitrate wlan0} in a conkyrc !

For the stripping of the mp/s, which conky variable gives you this result, for this second question the conky megathread is maybe more apropriate : [http://ubuntuforums.org/showthread.php?p=10600649#post10600649](http://ubuntuforums.org/showthread.php?p=10600649#post10600649)

---

### Post by Clicksights on 2011-03-28
wlourf, the wireless part IS included in the .conkyrc above....
did you miss it? :-p

Or did you mean what the output looks like?
thanks!

btw did post: [http://ubuntuforums.org/showpost.php?p=10612221&postcount=16778](http://ubuntuforums.org/showpost.php?p=10612221&postcount=16778)
with screenshot :-)

hope some one has a solution!

---

### Post by wlourf on 2011-03-29
ClickSight, to remove Mb/s for your ring, just add the red line in the Lua script, near the end 
```
function conky_clock_rings()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
[COLOR=Red]        if pt['name']=="wireless_bitrate" then str = str:gsub(" Mb/s","") end[/COLOR]
        value=tonumber(str)
        pct=value/pt['max']
        
        draw_ring(cr,pct,pt)
    end

....

```
hope this help (the first answer I've post a few days ago was for use with my scripts because they don't read conky variables on the same way).
I'll have a look at the other thread!

---

### Post by Clicksights on 2011-03-30
** Wlourf **Thankx so much again!
It worded like a dream!
:P

now at last i have a working not shifting Wifi info ring!
Seems the conky virus is getting to me too.
:lolflag:


>>edit if my Wifi is off/not connected i get an error:
```
Conky: llua_do_call: function conky_clock_rings execution failed: /home/user/.lua/scripts/clock_rings.lua:362: attempt to perform arithmetic on local 'value' (a nil value)
```

Any ideas???

on to the next edit, version 1.5 i believe ;)

Still have some fixes to do... Like WAN IP only showing up when there is a connection...
(the wlan0 and eth0 will both have to be checked)
 And that if i disconnect from my wlan, the ring stays at the last signal strength....
It doesn't drop to zero. :confused:  Any help there is welcome!
It does go back when i restart conky manually.

i am trying to learn as much as i can, and will find a way to keep also the system part on its designated place... i know i have to play with the if else statements... so give me a few days and i will have an update again. 

Thankx again for your help!

PS
the thing i don't get, this is the support part of the Cony forum threat, and you are doing a hell of a good job! The other one is to show off.... than why is everybody over there mostly giving support? 
And not just showing their conky's??? LOL

---

### Post by Clicksights on 2011-03-30
:D update; i fixed the moving off the system info part!
used ${else}${voffset 14} (could be 15 :) ) in the end if statement in the Net section.

And changed the credits too! 
you deserve a place in it!
laterz

---

### Post by wlourf on 2011-03-30
> **Clicksights said:**
> 


>>edit if my Wifi is off/not connected i get an error:
```
Conky: llua_do_call: function conky_clock_rings execution failed: /home/user/.lua/scripts/clock_rings.lua:362: attempt to perform arithmetic on local 'value' (a nil value)
```Any ideas???
yes, when your wifi is not connected, the returned value is **nil**, so you can change it to zero with the red line :
```
    local function setup_rings(cr,pt)
        local str=''
        local value=0
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
        if pt['name']=="wireless_bitrate" then str = str:gsub(" Mb/s","") end
        value=tonumber(str)
[COLOR=Red]        if value == nil then value = 0 end[/COLOR]
        pct=value/pt['max']
        
        draw_ring(cr,pct,pt)
    end
```

I think this line should solve the problem of signal strength after disconnecting.

Well, I think this thread is more Lua specific. It started when Lua was not so popular :)

---

### Post by Clicksights on 2011-03-31
**wlourf**

Once again you gave me the solution....
I am very thankfull!

.lua is still a hard part too learn, but i will try!
I am so glad this all works now!!!

:popcorn:

have a beer/rum/smoke extra tonight you deserve it!

:D

>>in case you dont do any off those, pick something your self! LOL

---

### Post by wlourf on 2011-03-31
you're welcome clicksight :D

if you are interessted in Cairo and Lua, you can find some interesting links here :
[http://conky-pitstop.wikidot.com/conky-links](http://conky-pitstop.wikidot.com/conky-links)

with other links to get some inspiration !

---

### Post by Clicksights on 2011-03-31
You gave me too much reading! :)

I bookmarked it for the future...
I managed to fix the WAN IP only showing with the ${if_gw} statement!
Now the showing of the Network info works as i wanted.
\\:D/

So all works, only the bug in the wifi ring, that it stays at the last reception percentage, left to fix.

And if i want to be a real perfectionist, id did try but i am clueless as to where the problem is to be fixed:
if i have no connections at all, at turn on a connection and get the wan ip there is a shift in the system part at the bottom of about 1 pixel....

](*,)

---

### Post by wlourf on 2011-04-01
> **Clicksights said:**
> 
So all works, only the bug in the wifi ring, that it stays at the last reception percentage, left to fix.


Which ring is it ? is it in the script of this post : [http://ubuntuforums.org/showpost.php?p=10594070&postcount=290](http://ubuntuforums.org/showpost.php?p=10594070&postcount=290)

> **Clicksights said:**
> 
And if i want to be a real perfectionist, id did try but i am clueless as to where the problem is to be fixed:
if i have no connections at all, at turn on a connection and get the wan ip there is a shift in the system part at the bottom of about 1 pixel....

](*,)
No idea for that, did you try to use the $voffest statement ?

---

### Post by Clicksights on 2011-04-02
will post later.
i will have to copy my conky and lua, it changed a bit since the last data dump...
and now i am going too sleep till my mind is cleared from all the good things in life...
it was a good Friday night party! lol!

cya

---

### Post by akernan on 2011-04-02
I use bash scripts to parse my wireless signal info from /proc/net/wireless, use the execbar/execgraph in conky to display.  The wireless signal/noise is regularly above 100, that's the threshold for the conky variables.  The conky wireless variables do not work, I think it's caused by the Broadcom drivers.  How can I parse this signal info from /proc/net/wireless with lua and display it with bars or graphs?  Does conky have a variable that I can use ?

---

### Post by akernan on 2011-04-02
> **akernan said:**
> I use bash scripts to parse my wireless signal info from /proc/net/wireless, use the execbar/execgraph in conky to display.  The wireless signal/noise is regularly above 100, that's the threshold for the conky variables.  The conky wireless variables do not work, I think it's caused by the Broadcom drivers.  How can I parse this signal info from /proc/net/wireless with lua and display it with bars or graphs?  Does conky have a variable that I can use ?

I solved my problem.  I was able to modify the bargraph.lua script from wlourf.

---

### Post by Clicksights on 2011-04-04
Well it took a day or 2 longer... :)
But had a nice weekend! 

Here it is.
The Conky-Orange-Ubuntu

The only 3 bugs left:
-wifi doesn't go back too 0%  if turned off.
-there is a shift of about 1 pixel when WAN IP comes up.
-if already connected to the cable, conky doesn't start up the eth0 interface,
after pulling the cable out, end put it back in it does come up...

i put in a read me file, any comments are welcome!

BTW solution are also welcome :P

---

### Post by wlourf on 2011-04-05
> **Clicksights said:**
> 
-wifi doesn't go back too 0%  if turned off.

Maybe there are other ways, but this one works :
```
    local function setup_rings(cr,pt)
        local str=''
        local value=0
        
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
        if pt['name']=="wireless_bitrate" then str = str:gsub(" Mb/s","") end
[COLOR=Red]        if (pt['name']=="wireless_link_qual" or pt['name']=="wireless_bitrate") and conky_parse("${wireless_essid wlan0}") == "off/any" then
            --not connected : set two rings (link_qual & bitrate) to zero
            --have to do the same in conkyrc, I believe, something like
            --${if_match "${wireless_essid wlan0}" == "off/any"}no wifi${else}${wireless_link_qual wlan0}%${endif}
               str = 0
           end
[/COLOR]        value=tonumber(str)

    
    if value == nil then value = 0 end
        pct=value/pt['max']
        draw_ring(cr,pct,pt)
    end
```> 
-there is a shift of about 1 pixel when WAN IP comes up.
-if already connected to the cable, conky doesn't start up the eth0 interface,
after pulling the cable out, end put it back in it does come up...

i put in a read me file, any comments are welcome!

BTW solution are also welcome :PDidn't see the offset (I don't have your fonts) and there is no problem when eth0 is on before conky starts (but I don't use ubuntu (Crunchbang Power :D)

Good luck for your next Conky !

---

### Post by Clicksights on 2011-04-06
:D i use ubuntu netbook, so could be due to that...
I will have to try if blackbunbtu does the same, i havent installed conky on the usb drive yet.

I will try the wifi solution, hope it works.
A variation of this one for the small screen is in the make, but didn't have enough inspiration yet to begin.
(Maybe in the next ubuntu netbook there is a possibility to adjust the screen resolution to a higher one.
In M$ it is possible, but just in this distro not...(mmm will try in blackbuntu come too think of it) and to be honest i like it enough too wait. i already wasted 2 days trying to change the menu on my netbook, just too find out it is not possible yet... :confused: so i will wait and if it's not better in the next release i will switch to something else completely)

i checked my conky, but the output of the wifi does go back to 0 in conky, just not in the ring.
I will play around and let you know, tonight i am to busy.

let you know soon!

---

### Post by yiannis66 on 2011-07-25
hello, I need some help in a conky ( I have no idea of programming)
The idea is to make a car cabin looks active it.
I have this photo  and so far I make the counter working with a conky of "olgmen"
[IMG]http://img221.imageshack.us/img221/57/screenshot3re.png[/IMG]
As u can see i remove the arrow from the speedmeter and i replace it with the CPU.
But I don't know how can i move the temp out of the place is now  and I will like to put it 
left on the place that shows in the photo.
this is the conkyrc
```
# main conkyrc by Boris Krinkel <olgmen>
# krinkel@rambler.ru
# --- &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1099; &#1086;&#1082;&#1085;&#1072; ---
# &#1101;&#1090;&#1080; &#1089;&#1090;&#1088;&#1086;&#1082;&#1080; &#1085;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1099; &#1076;&#1083;&#1103; &#1085;&#1086;&#1088;&#1084;&#1072;&#1083;&#1100;&#1085;&#1086;&#1081; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099; &#1083;&#1091;&#1095;&#1096;&#1077; &#1085;&#1077; &#1080;&#1079;&#1084;&#1077;&#1085;&#1103;&#1090;&#1100;
own_window		yes
# &#1076;&#1083;&#1103; &#1074;&#1099;&#1074;&#1086;&#1076;&#1072; &#1092;&#1086;&#1085;&#1072; &#1088;&#1072;&#1089;&#1082;&#1086;&#1084;&#1084;&#1077;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1090;&#1100; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1091;&#1102; &#1089;&#1090;&#1088;&#1086;&#1082;&#1091;, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090;&#1100; &#1094;&#1074;&#1077;&#1090;, &#1074; &#1076;&#1072;&#1085;&#1085;&#1099;&#1081; &#1084;&#1086;&#1084;&#1077;&#1085;&#1090; &#1082;&#1088;&#1072;&#1089;&#1085;&#1099;&#1081; &#1080; &#1074; &#1089;&#1090;&#1088;&#1086;&#1082;&#1077; own_window_transparent &#1087;&#1088;&#1086;&#1087;&#1080;&#1089;&#1072;&#1090;&#1100; no
#own_window_colour ff0000
own_window_class	Conky 
own_window_transparent	yes 
own_window_type		override 
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager 
# &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1099; &#1084;&#1086;&#1078;&#1085;&#1086; &#1080;&#1079;&#1084;&#1077;&#1085;&#1103;&#1090;&#1100;
# &#1084;&#1080;&#1085;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;
minimum_size 2010 0 
# &#1084;&#1080;&#1085;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1096;&#1080;&#1088;&#1080;&#1085;&#1072;
maximum_width 1350 
# --- &#1088;&#1072;&#1089;&#1087;&#1086;&#1083;&#1086;&#1078;&#1077;&#1085;&#1080;&#1077; &#1086;&#1082;&#1085;&#1072;
# &#1083;&#1077;&#1074;&#1099;&#1081; &#1074;&#1077;&#1088;&#1093;&#1085;&#1080;&#1081; &#1091;&#1075;&#1086;&#1083; &#1101;&#1082;&#1088;&#1072;&#1085;&#1072; 
alignment top_left 
# &#1083;&#1077;&#1074;&#1099;&#1081; &#1085;&#1080;&#1078;&#1085;&#1080;&#1081; &#1091;&#1075;&#1086;&#1083; &#1101;&#1082;&#1088;&#1072;&#1085;&#1072;
#alignment bottom_left 
# &#1087;&#1088;&#1072;&#1074;&#1099;&#1081; &#1074;&#1077;&#1088;&#1093;&#1085;&#1080;&#1081; &#1091;&#1075;&#1086;&#1083; &#1101;&#1082;&#1088;&#1072;&#1085;&#1072;
#alignment top_right 
# &#1087;&#1088;&#1072;&#1074;&#1099;&#1081; &#1085;&#1080;&#1078;&#1085;&#1080;&#1081; &#1091;&#1075;&#1086;&#1083; &#1101;&#1082;&#1088;&#1072;&#1085;&#1072;
#alignment bottom_right 
# &#1088;&#1072;&#1089;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1077; &#1084;&#1077;&#1078;&#1076;&#1091; &#1082;&#1088;&#1086;&#1084;&#1082;&#1086;&#1081; &#1101;&#1082;&#1088;&#1072;&#1085;&#1072; &#1080; &#1086;&#1082;&#1085;&#1086;&#1084;
# &#1087;&#1086; &#1075;&#1086;&#1088;&#1080;&#1079;&#1086;&#1085;&#1090;&#1072;&#1083;&#1080;
gap_x 650 
# &#1087;&#1086; &#1074;&#1077;&#1088;&#1090;&#1080;&#1082;&#1072;&#1083;&#1080;
gap_y 225

# --- &#1075;&#1088;&#1072;&#1092;&#1080;&#1082;&#1072; &#1086;&#1082;&#1085;&#1072; --- 
# &#1077;&#1089;&#1083;&#1080; &#1078;&#1077;&#1083;&#1072;&#1077;&#1090;&#1077; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090;&#1100; conky &#1085;&#1072; &#1076;&#1088;&#1091;&#1075;&#1086;&#1084; &#1092;&#1086;&#1085;&#1077; &#1085;&#1072;&#1087;&#1080;&#1096;&#1080;&#1090;&#1077; yes
background no
# &#1086;&#1082;&#1072;&#1085;&#1090;&#1086;&#1074;&#1082;&#1072; &#1086;&#1082;&#1085;&#1072;, &#1073;&#1086;&#1088;&#1076;&#1102;&#1088;
draw_borders no
# &#1077;&#1089;&#1083;&#1080; &#1073;&#1086;&#1088;&#1076;&#1102;&#1088; yes
# &#1076;&#1083;&#1080;&#1085;&#1072; &#1096;&#1090;&#1088;&#1080;&#1093;&#1086;&#1074; &#1073;&#1086;&#1088;&#1076;&#1102;&#1088;&#1072;, &#1077;&#1089;&#1083;&#1080; 0, &#1090;&#1086; &#1073;&#1086;&#1088;&#1076;&#1102;&#1088; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090;&#1089;&#1103; &#1089;&#1087;&#1083;&#1086;&#1096;&#1085;&#1086;&#1081; &#1083;&#1080;&#1085;&#1080;&#1077;&#1081;
stippled_borders 1
# &#1090;&#1086;&#1083;&#1097;&#1080;&#1085;&#1072; &#1083;&#1080;&#1085;&#1080;&#1081; &#1073;&#1086;&#1088;&#1076;&#1102;&#1088;&#1072; 
border_width 1
# &#1073;&#1086;&#1088;&#1076;&#1102;&#1088; &#1074;&#1086;&#1082;&#1088;&#1091;&#1075; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084;&#1099;&#1093; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082;&#1086;&#1074;
draw_graph_borders no
# &#1074;&#1082;&#1083;&#1102;&#1095;&#1080;&#1090;&#1100; &#1090;&#1077;&#1085;&#1100;?
draw_shades no
# &#1086;&#1082;&#1072;&#1085;&#1090;&#1086;&#1074;&#1082;&#1072; &#1074;&#1086;&#1082;&#1088;&#1091;&#1075; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072; &#1080; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084;&#1099;&#1093; &#1086;&#1073;&#1098;&#1077;&#1082;&#1090;&#1086;&#1074;
draw_outline no 
# &#1044;&#1086;&#1073;&#1072;&#1074;&#1080;&#1090;&#1100; &#1087;&#1088;&#1086;&#1073;&#1077;&#1083;?  &#1058;&#1086;&#1083;&#1100;&#1082;&#1086; &#1076;&#1083;&#1103; &#1074;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1084;&#1099;&#1093; &#1086;&#1073;&#1098;&#1077;&#1082;&#1090;&#1086;&#1074; 
use_spacer right 

# --- &#1094;&#1074;&#1077;&#1090; ---
# &#1086;&#1089;&#1085;&#1086;&#1074;&#1085;&#1086;&#1081; &#1094;&#1074;&#1077;&#1090; &#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102; 
default_color DeepSkyBlue
# &#1094;&#1074;&#1077;&#1090; &#1090;&#1077;&#1085;&#1080;
default_shade_color black 
# &#1094;&#1074;&#1077;&#1090; &#1086;&#1082;&#1072;&#1085;&#1090;&#1086;&#1074;&#1082;&#1080;
default_outline_color black
# &#1076;&#1086;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1077;&#1083;&#1100;&#1085;&#1099;&#1077;
color1 white
color2 yellow 
color3 red 
color4 green
# --- &#1096;&#1088;&#1080;&#1092;&#1090;&#1099; ---
# &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1084;&#1099;&#1077; &#1096;&#1088;&#1080;&#1092;&#1090;&#1099; X &#1082;&#1086;&#1075;&#1076;&#1072; Xft &#1085;&#1077; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103;, &#1084;&#1086;&#1078;&#1085;&#1086; &#1074;&#1099;&#1073;&#1088;&#1072;&#1090;&#1100; &#1086;&#1076;&#1080;&#1085; &#1080;&#1079; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; 
#font 5x7 
#font 6x10 
#font 7x13 
#font 8x13 
#font 9x15 
#font *mintsmild.se* 
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-* 

# &#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1083;&#1080; Xft? 
use_xft yes 

# &#1064;&#1088;&#1080;&#1092; Xft &#1082;&#1086;&#1075;&#1076;&#1072; Xft &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;&#1085;, &#1079;&#1076;&#1077;&#1089;&#1100; &#1084;&#1086;&#1078;&#1085;&#1086; &#1074;&#1074;&#1077;&#1089;&#1090;&#1080; &#1085;&#1072;&#1079;&#1074;&#1072;&#1085;&#1080;&#1077; &#1080; &#1088;&#1072;&#1079;&#1084;&#1077;&#1088; &#1083;&#1102;&#1073;&#1086;&#1075;&#1086; &#1096;&#1088;&#1080;&#1092;&#1090;&#1072; 
xftfont PT Sans:size=9 

# &#1103;&#1088;&#1082;&#1086;&#1089;&#1090;&#1100; &#1096;&#1088;&#1080;&#1092;&#1090;&#1072; &#1087;&#1088;&#1080; &#1080;&#1089;&#1087;&#1086;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1080;&#1080; &#1096;&#1088;&#1080;&#1092;&#1090;&#1086;&#1074; Xft 
xftalpha 0.5 
# &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090;&#1100; &#1074;&#1077;&#1089;&#1100; &#1090;&#1077;&#1082;&#1089;&#1090; &#1087;&#1088;&#1086;&#1087;&#1080;&#1089;&#1085;&#1099;&#1084;&#1080; &#1073;&#1091;&#1082;&#1074;&#1072;&#1084;&#1080; 
uppercase no 
# &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1100; &#1082;&#1086;&#1076;&#1080;&#1088;&#1086;&#1074;&#1082;&#1091; UTF8? &#1055;&#1056;&#1048;&#1052;&#1045;&#1063;&#1040;&#1053;&#1048;&#1045;: &#1090;&#1088;&#1077;&#1073;&#1091;&#1077;&#1090;&#1089;&#1103; Xft 
override_utf8_locale yes 

# --- &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077; &#1085;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1099; &#1076;&#1083;&#1103; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099;
# &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1077; &#1074; &#1089;&#1077;&#1082;&#1091;&#1085;&#1076;&#1072;&#1093; &#1085;&#1077; &#1080;&#1084;&#1077;&#1077;&#1090; &#1089;&#1084;&#1099;&#1089;&#1083;&#1072; &#1089;&#1090;&#1072;&#1074;&#1080;&#1090;&#1100; &#1073;&#1086;&#1083;&#1100;&#1096;&#1077; 2
# &#1087;&#1088;&#1080; &#1074;&#1099;&#1074;&#1086;&#1076;&#1077; &#1074;&#1088;&#1077;&#1084;&#1077;&#1085;&#1080; &#1074; &#1089;&#1077;&#1082;&#1091;&#1085;&#1076;&#1072;&#1093; &#1085;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1086; &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1077; 1 &#1080; &#1084;&#1077;&#1085;&#1077;&#1077;
update_interval 0.5 
# &#1074;&#1088;&#1077;&#1084;&#1103; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099; &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;&#1099; &#1076;&#1086; &#1077;&#1105; &#1074;&#1099;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1080;&#1103;
# &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090;&#1077; 0 &#1076;&#1083;&#1103; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099; &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;&#1099; &#1073;&#1077;&#1079; &#1086;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1080;
total_run_times 0
# &#1076;&#1074;&#1086;&#1081;&#1085;&#1072;&#1103; &#1073;&#1091;&#1092;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103; (&#1090;&#1088;&#1077;&#1073;&#1091;&#1077;&#1090;&#1089;&#1103; &#1076;&#1083;&#1103; flicker, &#1084;&#1086;&#1078;&#1077;&#1090; &#1085;&#1077; &#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100;) 
double_buffer yes 
# &#1074;&#1099;&#1095;&#1080;&#1090;&#1072;&#1090;&#1100; &#1073;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1102; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074;&#1086;&#1081; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1099; &#1080;&#1079; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1084;&#1086;&#1081; &#1087;&#1072;&#1084;&#1103;&#1090;&#1080;? 
no_buffers yes 
# &#1082;&#1086;&#1083;&#1080;&#1095;&#1077;&#1089;&#1090;&#1074;&#1086; cpu
cpu_avg_samples 2
# number of net samples to average 
net_avg_samples 2 
imlib_cache_size 0 
short_units yes 
pad_percents 2 
text_buffer_size 2048 
imlib_cache_size 0 


#--- LUA ---
lua_load ~/olgmen_scale.lua
lua_draw_hook_pre widgets

# ----------------------- &#1055;&#1056;&#1048;&#1052;&#1045;&#1063;&#1040;&#1053;&#1048;&#1071; --------------------------------
#
# &#1055;&#1077;&#1088;&#1074;&#1072;&#1103; &#1089;&#1090;&#1088;&#1086;&#1082;&#1072; &#1087;&#1086;&#1089;&#1083;&#1077; TEXT &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090; &#1074;&#1088;&#1077;&#1084;&#1103; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099; &#1087;&#1086;&#1089;&#1083;&#1077; &#1074;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1080;&#1103; &#1082;&#1086;&#1084;&#1087;&#1100;&#1102;&#1090;&#1077;&#1088;&#1072;. &#1055;&#1086;&#1089;&#1083;&#1077; &#1076;&#1074;&#1091;&#1093; &#1095;&#1072;&#1089;&#1086;&#1074; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099;
# &#1085;&#1072;&#1076;&#1087;&#1080;&#1089;&#1100; "&#1056;&#1072;&#1073;&#1086;&#1090;&#1072;&#1102;: 2h 00m 00s" &#1079;&#1072;&#1084;&#1077;&#1085;&#1103;&#1077;&#1090;&#1089;&#1103; &#1085;&#1072; &#1084;&#1080;&#1075;&#1072;&#1102;&#1097;&#1091;&#1102; &#1085;&#1072;&#1076;&#1087;&#1080;&#1089;&#1100; "&#1055;&#1054;&#1056;&#1040; &#1054;&#1058;&#1044;&#1054;&#1061;&#1053;&#1059;&#1058;&#1068;".
# &#1042;&#1088;&#1077;&#1084;&#1103; &#1084;&#1086;&#1078;&#1085;&#1086; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090; &#1080;&#1079;&#1084;&#1077;&#1085;&#1080;&#1074; "2h 00m 00s" &#1085;&#1072; &#1083;&#1102;&#1073;&#1086;&#1077; &#1076;&#1088;&#1091;&#1075;&#1086;&#1077;, &#1085;&#1086; &#1074; &#1090;&#1086;&#1084; &#1078;&#1077; &#1092;&#1086;&#1088;&#1084;&#1072;&#1090;&#1077;.
# &#1045;&#1089;&#1083;&#1080; &#1090;&#1072;&#1082;&#1086;&#1081; "&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;" &#1085;&#1077; &#1085;&#1091;&#1078;&#1077;&#1085; &#1090;&#1086; &#1087;&#1077;&#1088;&#1074;&#1091;&#1102; &#1089;&#1090;&#1088;&#1086;&#1082;&#1091; &#1087;&#1088;&#1080;&#1074;&#1077;&#1076;&#1080;&#1090;&#1077; &#1082; &#1090;&#1072;&#1082;&#1086;&#1084;&#1091; &#1074;&#1080;&#1076;&#1091;
#
# ${goto 100}${voffset 40}${font PT Sans:Bold:size=12}&#1056;&#1072;&#1073;&#1086;&#1090;&#1072;&#1102;: $uptime
#


TEXT
${voffset -20}${cpu cpu}
#${voffset 20}${color DC143C}${font PT Sans:Bold:size=27}${time %H}
#${voffset -8}${font PT Sans:Bold:size=20}${time :%M}${voffset -6}${font PT Sans:Bold:size=12}${time :%S}${goto 180}${voffset -2}${font PT Sans:Bold:size=10}${if_match "${uptime}" > "4h 00m 00s"}${color ff0000}
#${goto 200}${blink &#937;&#929;&#913; &#915;&#921;&#913; &#933;&#928;&#925;&#927;}${else}ANOIXTO: $uptime${endif}
#${goto 105}${voffset 10}${execpi 3600 ~/week1.sh}
${voffset 200}


```
and the lua is 
```
--[[
Conky Widgets by olgmen (04.2010)

&#1076;&#1083;&#1103; &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072; &#1085;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1086; &#1074;&#1074;&#1077;&#1089;&#1090;&#1080; &#1076;&#1086; TEXT &#1089;&#1076;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1089;&#1090;&#1088;&#1086;&#1082;&#1080;

#--- LUA ---
lua_load ~/scripts/olgmen_scale.lua
lua_draw_hook_pre widgets

&#1087;&#1088;&#1080; &#1091;&#1089;&#1083;&#1086;&#1074;&#1080;&#1080;, &#1095;&#1090;&#1086; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090; olgmen_scale.lua &#1089;&#1086;&#1093;&#1088;&#1072;&#1085;&#1077;&#1085; &#1074; &#1087;&#1072;&#1087;&#1082;&#1077; ~/scripts
]]

require 'cairo'

-- ------------------------------------------------------------------------

--[[ DISK ]]

function scale (cr, x, y, radius, stat, max, element, width, gap, cap, start_angle, end_angle, bgc, bga, fgc, fga)

-- &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1103; &#1087;&#1077;&#1088;&#1077;&#1082;&#1086;&#1076;&#1080;&#1088;&#1086;&#1074;&#1082;&#1080; &#1094;&#1074;&#1077;&#1090;&#1072;

		function rgb_to_r_g_b(colour,alpha)
		return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
		end

-- &#1079;&#1072;&#1073;&#1080;&#1088;&#1072;&#1077;&#1084; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077; &#1080;&#1079; &#1054;&#1057;


		local value = tonumber(conky_parse(stat))
		if value == nil then value = 0 end
		local pct = value/max

-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1090;&#1086;&#1083;&#1097;&#1080;&#1085;&#1091; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084;&#1099;&#1093; &#1083;&#1080;&#1085;&#1080;&#1081;

		local s_th = 2

-- &#1086;&#1089;&#1085;&#1086;&#1074;&#1085;&#1099;&#1077; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077;

--[[
	&#1087;&#1077;&#1088;&#1077;&#1074;&#1086;&#1076;&#1080;&#1084; &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1077; &#1091;&#1075;&#1083;&#1086;&#1074; &#1074; &#1088;&#1072;&#1076;&#1080;&#1072;&#1083;&#1100;&#1085;&#1091;&#1102; &#1084;&#1077;&#1088;&#1091; start_angle * (math.pi / 180)

	&#1090;&#1086;&#1095;&#1082;&#1072; &#1085;&#1072;&#1095;&#1072;&#1083;&#1072; &#1074;&#1099;&#1074;&#1086;&#1076;&#1072; &#1086;&#1082;&#1088;&#1091;&#1085;&#1086;&#1089;&#1090;&#1080;, &#1074; lua+cairo &#1088;&#1072;&#1089;&#1087;&#1086;&#1083;&#1086;&#1078;&#1077;&#1085;&#1072; &#1085;&#1072; &#1082;&#1086;&#1086;&#1088;&#1076;&#1080;&#1085;&#1072;&#1090;&#1077; &#1061;, &#1087;&#1077;&#1088;&#1077;&#1074;&#1086;&#1076;&#1080;&#1084; &#1085;&#1072; Y

	start_angle * (math.pi/180) - math.pi / 2 -- &#1087;&#1086;&#1074;&#1086;&#1088;&#1086;&#1090; &#1074;&#1083;&#1077;&#1074;&#1086; &#1085;&#1072; 90 &#1075;&#1088;&#1072;&#1076;&#1091;&#1089;&#1086;&#1074; &#1080;&#1083;&#1080; &#1085;&#1072; 1/4 &#1082;&#1088;&#1091;&#1075;&#1072;
]]

-- &#1085;&#1072;&#1095;&#1072;&#1083;&#1086; &#1076;&#1091;&#1075;&#1080;
		local sa = start_angle * (math.pi / 215) - math.pi / 2
-- &#1082;&#1086;&#1085;&#1077;&#1094; &#1076;&#1091;&#1075;&#1080;
		local ea =   end_angle * (math.pi / 215) - math.pi / 2

-- &#1088;&#1072;&#1089;&#1095;&#1080;&#1090;&#1099;&#1074;&#1072;&#1077;&#1084; &#1076;&#1083;&#1080;&#1085;&#1091; &#1076;&#1091;&#1075;&#1080; end_angle &#1076;&#1086;&#1083;&#1078;&#1077;&#1085; &#1074;&#1089;&#1077;&#1075;&#1076;&#1072; &#1073;&#1099;&#1090;&#1100; &#1073;&#1086;&#1083;&#1100;&#1096;&#1077; start_angle

		local angle = ea - sa	-- &#1094;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1091;&#1075;&#1086;&#1083; &#1076;&#1091;&#1075;&#1080;

-- &#1082;&#1086;&#1083;&#1080;&#1095;&#1077;&#1089;&#1090;&#1074;&#1086; &#1079;&#1072;&#1079;&#1086;&#1088;&#1086;&#1074; &#1084;&#1077;&#1078;&#1076;&#1091; &#1101;&#1083;&#1077;&#1084;&#1077;&#1085;&#1090;&#1072;&#1084;&#1080;

		amount_gap = element - 1

-- &#1086;&#1073;&#1097;&#1072;&#1103; &#1096;&#1080;&#1088;&#1080;&#1085;&#1072; &#1079;&#1072;&#1079;&#1086;&#1088;&#1086;&#1074;

		place_of_amount_gap = amount_gap * gap

-- &#1084;&#1077;&#1089;&#1090;&#1086; &#1079;&#1072;&#1085;&#1080;&#1084;&#1072;&#1077;&#1084;&#1086;&#1077; &#1101;&#1083;&#1077;&#1084;&#1077;&#1085;&#1090;&#1072;&#1084;&#1080;

		place_of_amount_element = end_angle - start_angle - place_of_amount_gap

-- &#1096;&#1080;&#1088;&#1080;&#1085;&#1072; &#1086;&#1076;&#1085;&#1086;&#1075;&#1086; &#1101;&#1083;&#1077;&#1084;&#1077;&#1085;&#1090;&#1072;

		width_of_element = place_of_amount_element / element

-- &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084; &#1076;&#1091;&#1075;&#1091; &#1076;&#1083;&#1103; &#1092;&#1086;&#1085;&#1072;
		local i = 0
-- &#1076;&#1077;&#1083;&#1077;&#1085;&#1080;&#1103; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084; &#1095;&#1077;&#1088;&#1077;&#1079; &#1088;&#1072;&#1089;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1077; &#1088;&#1072;&#1074;&#1085;&#1086;&#1077; &#1096;&#1080;&#1088;&#1080;&#1085;&#1077; &#1101;&#1083;&#1077;&#1084;&#1077;&#1085;&#1090;&#1072;+&#1079;&#1072;&#1079;&#1086;&#1088;&#1072; &#1084;&#1077;&#1078;&#1076;&#1091; &#1101;&#1083;&#1077;&#1084;&#1077;&#1085;&#1090;&#1072;&#1084;&#1080;
		local winkel = math.rad(width_of_element+gap)
-- &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084; element &#1076;&#1077;&#1083;&#1077;&#1085;&#1080;&#1081; &#1076;&#1083;&#1103; &#1092;&#1086;&#1085;&#1072;
		for i=0,element-1,1 do
-- &#1091;&#1089;&#1090;&#1072;&#1085;&#1072;&#1074;&#1083;&#1080;&#1074;&#1072;&#1077;&#1084; &#1090;&#1086;&#1083;&#1097;&#1080;&#1085;&#1091; &#1076;&#1077;&#1083;&#1077;&#1085;&#1080;&#1081; 
		cairo_set_line_width(cr,width_of_element)
-- &#1074;&#1080;&#1076; &#1076;&#1077;&#1083;&#1077;&#1085;&#1080;&#1081;
		cairo_set_line_cap  (cr, cap)
-- &#1079;&#1072;&#1076;&#1072;&#1077;&#1084; &#1094;&#1074;&#1077;&#1090; &#1076;&#1083;&#1103; &#1092;&#1086;&#1085;&#1072;
		cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
-- &#1082;&#1086;&#1086;&#1088;&#1076;&#1080;&#1085;&#1072;&#1090;&#1099; &#1085;&#1072;&#1095;&#1072;&#1083;&#1100;&#1085;&#1099;&#1093; &#1090;&#1086;&#1095;&#1077;&#1082;
		cairo_move_to(cr, x+math.cos(sa+winkel*i)*radius, y+math.sin(sa+winkel*i)*radius)
-- &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084; &#1076;&#1077;&#1083;&#1077;&#1085;&#1080;&#1103;
		cairo_line_to(cr, x+math.cos(sa+winkel*i)*(radius+width), y+math.sin(sa+winkel*i)*(radius+width))
		cairo_stroke(cr)
		end

		local proc = value / (max/element)

-- &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084; &#1076;&#1091;&#1075;&#1091; &#1080;&#1085;&#1076;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088;&#1072;
		for i=0,proc,1 do
-- &#1079;&#1072;&#1076;&#1072;&#1077;&#1084; &#1094;&#1074;&#1077;&#1090; &#1076;&#1083;&#1103; element
		cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc, fga))
-- &#1082;&#1086;&#1086;&#1088;&#1076;&#1080;&#1085;&#1072;&#1090;&#1099; &#1085;&#1072;&#1095;&#1072;&#1083;&#1100;&#1085;&#1099;&#1093; &#1090;&#1086;&#1095;&#1077;&#1082;
		cairo_move_to(cr, x+math.cos(sa+winkel*i)*radius, y+math.sin(sa+winkel*i)*radius)
-- &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084; &#1076;&#1077;&#1083;&#1077;&#1085;&#1080;&#1103;
		cairo_line_to(cr, x+math.cos(sa+winkel*i)*(radius+width), y+math.sin(sa+winkel*i)*(radius+width))
		cairo_stroke(cr)
		end
-- &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1072; --------------------------------------

		function hand(a_trame,arc,arc0,arc1,lg,r,border,rgb)

		xx = xc + radius*math.sin(arc)*lg
		yy = yc - radius*math.cos(arc)*lg
		x0 = xc + r*math.sin(arc0)
		y0 = yc - r*math.cos(arc0)
		x1 = xc + r*math.sin(arc1)
		y1 = yc - r*math.cos(arc1)

		cairo_set_line_width(cr,1)
		cairo_set_source_rgba(cr,border[1],border[2],border[3],0.5)
		cairo_move_to (cr, x0, y0)
		cairo_curve_to (cr, x0, y0, xx, yy, x1, y1)
		cairo_arc(cr,xc,yc,r,arc1-math.pi,arc0-math.pi)
		cairo_stroke(cr)

-- &#1088;&#1080;&#1089;&#1091;&#1077;&#1084; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1091;

		cairo_move_to (cr, x0, y0)
		cairo_curve_to (cr, x0, y0, xx, yy, x1, y1)
		cairo_arc(cr,xc,yc,r,arc1-math.pi,arc0-math.pi)
		pat = cairo_pattern_create_radial (xc, yc, radius/10, xc, yc, radius*lg)
		cairo_pattern_add_color_stop_rgba (pat,0, rgb[1], rgb[2], rgb[3], 1)
		cairo_pattern_add_color_stop_rgba (pat, 1, 0, 0, 0, 1)
		cairo_set_source (cr, pat)
		cairo_fill (cr)
		cairo_pattern_destroy (pat)
		end

-- &#1047;&#1076;&#1077;&#1089;&#1100; &#1074;&#1074;&#1086;&#1076;&#1103;&#1090;&#1089;&#1103; &#1086;&#1089;&#1085;&#1086;&#1074;&#1085;&#1099;&#1077; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077;

-- &#1082;&#1086;&#1086;&#1088;&#1076;&#1080;&#1085;&#1072;&#1090;&#1099; &#1086;&#1089;&#1080; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1080;

		xc = x
		yc = y

-- &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;&#1099; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1080;, &#1087;&#1077;&#1088;&#1074;&#1072;&#1103; &#1094;&#1080;&#1092;&#1088;&#1072; &#1096;&#1080;&#1088;&#1080;&#1085;&#1072;, &#1074;&#1090;&#1086;&#1088;&#1072;&#1103; - &#1076;&#1083;&#1080;&#1085;&#1072;

		rs, lgs=4, 2.5	-- &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1072;

-- &#1088;&#1072;&#1089;&#1095;&#1077;&#1090; &#1091;&#1075;&#1083;&#1072; &#1076;&#1074;&#1080;&#1078;&#1077;&#1085;&#1080;&#1103; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1080;

		gamma = math.pi/2-math.atan(rs/(radius*lgs))
		secs_arc = ((120*math.pi/150)/max)* value-(118*math.pi/150)
		secs_arc0=secs_arc-gamma
		secs_arc1=secs_arc+gamma

-- &#1074;&#1099;&#1074;&#1086;&#1076; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1080;

		hand(alpha_trame,secs_arc,secs_arc0,secs_arc1,lgs,rs,{0,0,0},{.8,.8,.8})

end
-- -------------------------------------------

--[[ TEXT WIDGET &#1087;&#1088;&#1103;&#1084;&#1086;&#1081; ]]

function text_widget(cr, x, y, prefix, stat, suffix, font, fsize, fgc, fga, rotation)

-- &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1103; &#1087;&#1077;&#1088;&#1077;&#1082;&#1086;&#1076;&#1080;&#1088;&#1086;&#1074;&#1082;&#1080; &#1094;&#1074;&#1077;&#1090;&#1072;

 	local function rgb_to_r_g_b(colour, alpha)
		return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end


-- &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1103; &#1076;&#1086;&#1073;&#1072;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103; &#1085;&#1077;&#1079;&#1085;&#1072;&#1095;&#1080;&#1097;&#1080;&#1093; &#1085;&#1091;&#1083;&#1077;&#1081;

	function addzero100(num)

		if tonumber(num) < 10 then
			return "00" .. num
		elseif tonumber(num) <100 then
			return "0" .. num
		else
			return num
		end
	end

-- &#1079;&#1072;&#1073;&#1080;&#1088;&#1072;&#1077;&#1084; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077; &#1080;&#1079; &#1054;&#1057;

	local value = tonumber(conky_parse(stat))

	if value == nil then value = 0 end

-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1096;&#1088;&#1080;&#1092;&#1090;

	cairo_select_font_face (cr, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_BOLD)


-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1088;&#1072;&#1079;&#1084;&#1077;&#1088; &#1096;&#1088;&#1080;&#1092;&#1090;&#1072;
	cairo_set_font_size (cr, fsize)
-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1090;&#1086;&#1095;&#1082;&#1091; &#1074;&#1099;&#1074;&#1086;&#1076;&#1072;	
	cairo_move_to(cr, x, y)
-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1094;&#1074;&#1077;&#1090; &#1096;&#1088;&#1080;&#1092;&#1090;&#1072;
	cairo_set_source_rgba(cr, rgb_to_r_g_b(fgc, fga))
-- &#1087;&#1086;&#1074;&#1086;&#1088;&#1072;&#1095;&#1080;&#1074;&#1072;&#1077;&#1084; &#1090;&#1077;&#1082;&#1089;&#1090;
	cairo_rotate (cr, rotation*math.pi/180)
-- &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084; &#1090;&#1077;&#1082;&#1089;&#1090;
	cairo_show_text(cr, prefix .. (addzero100(value)) .. suffix)
end
--[[ END TEXT WIDGET ]]
-- ----------------------------------------------------------------
--[[ TEXT WIDGET &#1082;&#1088;&#1091;&#1075;&#1086;&#1074;&#1086;&#1081; ]]

	function addzero100(num)

	if tonumber(num) == nil then return end

		if tonumber(num) < 10 then
			return "00" .. num
		elseif tonumber(num) <100 then
			return "0" .. num
		else
			return num
		end
	end

	function string:split(delimiter)

		local result = { }
		local from  = 1
		local delim_from, delim_to = string.find( self, delimiter, from  )
		while delim_from do
		table.insert( result, string.sub( self, from , delim_from-1 ) )
		from  = delim_to + 1
		delim_from, delim_to = string.find( self, delimiter, from  )
		end
		table.insert( result, string.sub( self, from  ) )
		return result
	end

	function circlewriting(cr, text, font, fsize, radi, horiz, verti, tred, tgreen, tblue, talpha, start, finish, var1)

		local inum=string.len(text)
		range=finish
		deg=(finish-start)/(inum-1)
		degrads=1*(math.pi/180)
		local textcut=string.gsub(text, ".", "%1@@@")
		texttable=string.split(textcut, "@@@")
		for i = 1,inum do
			ival=i
			interval=(degrads*(start+(deg*(i-1))))+var1
			interval2=degrads*(start+(deg*(i-1)))
			txs=0+radi*(math.sin(interval))
			tys=0-radi*(math.cos(interval))
			cairo_select_font_face (cr, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_BOLD);
			cairo_set_font_size (cr, fsize);
			cairo_set_source_rgba (cr, tred, tgreen, tblue, talpha);
			cairo_move_to (cr, txs+horiz, tys+verti);
			cairo_rotate (cr, interval2)
			cairo_show_text (cr, (texttable[i]))
			cairo_rotate (cr, -interval2)
		end
	end

	function circlewritingdown(cr, text, font, fsize, radi, horiz, verti, tred, tgreen, tblue, talpha, start, finish, var1)

		local inum=string.len(text)
		deg=(start-finish)/(inum-1)
		degrads=1*(math.pi/215)
		local textcut=string.gsub(text, ".", "%1@@@")
		texttable=string.split(textcut, "@@@")
		for i = 1,inum do
			ival=i
			interval=(degrads*(start-(deg*(i-1))))+var1
			interval2=degrads*(start-(deg*(i-1)))
			txs=0+radi*(math.sin(interval))
			tys=0-radi*(math.cos(interval))
			cairo_select_font_face (cr, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_BOLD);
			cairo_set_font_size (cr, fsize);
			cairo_set_source_rgba (cr, tred, tgreen, tblue, talpha);
			cairo_move_to (cr, txs+horiz, tys+verti);
			cairo_rotate (cr, interval2+(180*math.pi/180))
			cairo_show_text (cr, (texttable[i]))
			cairo_rotate (cr, -interval2-(180*math.pi/180))
		end
	end

	function conky_draw_text()

		local updates=conky_parse('${updates}')
		update_num=tonumber(updates)

--circlewriting variable

cpu=tonumber(conky_parse('${cpu cpu1}'))
if cpu == nil then cpu = 0 end
--text must be in quotes
text=("CPU 1 " .. (addzero100(cpu)) .. " %") 
--font name must be in quotes
font="PT Sans"
fontsize=12
radius=115
positionx=120
positiony=200
colorred=10
colorgreen=0
colorblue=0
coloralpha=1
--to set start and finish values for circlewriting, if the text will cross 0 degrees then you must calculate for 360+finish degrees
--eg if you want to go from 270 to 90, then you will input 270 to 450.  Finish has to be greater than start.
start=330
finish=380
letterposition=0
circlewriting(cr, text, font, fontsize, radius, positionx, positiony, colorred, colorgreen, colorblue, coloralpha, start, finish, letterposition)



	end
--[[ END TEXT WIDGET ]]
--------------------------------
function conky_widgets()
	if conky_window == nil then return end
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)

---------------------------------
-- &#1090;&#1077;&#1084;&#1087;&#1077;&#1088;&#1072;&#1090;&#1091;&#1088;&#1072; cpu1
cr = cairo_create(cs)
	scale (cr, 140, 160, 30, "${exec expr `cat /sys/bus/platform/devices/coretemp.0/temp1_input` / 1000}", 100, 20, 1, 5, CAIRO_LINE_CAP_BUTT, 270, 390, 0xc0c0c0, 0.5, 0xFF0000, 1)
--		       x,  y, radius,    name,  arg,  max,  bgc      bga     fgc  fga
text_widget(cr, 110, 175, "",  "${exec expr `cat /sys/bus/platform/devices/coretemp.0/temp1_input` / 1000}", " °C", "PT Sans", 10, 0xFF0000, 1, 0)
	cairo_destroy(cr)

-- cpu1
cr = cairo_create(cs)
	scale (cr, 120, 200, 100, "${cpu cpu1}", 100, 25, 1, 0.5, CAIRO_LINE_CAP_ROUND, 270, 390, 0xc0c0c0, 0.5, 0xFF00FF, 1)
--		       x,  y, radius,    name,  arg,  max,  bgc      bga     fgc  fga
	cairo_destroy(cr)





--[[ &#1042;&#1099;&#1074;&#1086;&#1076; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072; &#1087;&#1086; &#1082;&#1088;&#1091;&#1075;&#1091;, &#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1077; &#1074; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090;&#1077; ]]

	cr = cairo_create(cs)
	conky_draw_text()
	cairo_destroy(cr)

end
```

---

### Post by yiannis66 on 2011-07-27
[IMG]http://desmond.imageshack.us/Himg40/scaled.php?server=40&filename=screenshotyxc.png&res=medium[/IMG]
After a few test I make this by using two conkyrc.
Now I will like to know if I can make the horn working
It,s an idea of my children.I will like to make it for them.

---

### Post by RichardCain on 2011-08-20
I am having a problem with hddtemp.  When I use the following in conky, everything is OK:

```
${hddtemp /dev/sda}°C
```

but when I call hddtemp in clock_rings.lua then it all goes awry; both the ring and text only read for 1 second out of 5 or 6, the text shows "N/A" the rest of the time.

conky -v:
```
$ conky -v
Conky 1.8.0 compiled Fri Apr 23 10:38:37 UTC 2010 for Linux 2.6.24-27-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2
```

scripts attached

---

### Post by RichardCain on 2011-08-20
Update - when conky is run in a terminal, it constantly returns:
```
Conky: llua_do_call: function conky_clock_rings execution failed: /home/richard/.conky/scripts/clock_rings.lua:328: attempt to perform arithmetic on local 'value' (a nil value)
```

Line 328 of said file is:
```
        pct=value/pt['max']
```

Hope this helps!

---

### Post by RichardCain on 2011-08-23
bump

---

### Post by birkopf on 2011-08-23
> **RichardCain said:**
> bump

Dear Richard,

For some reason conky always shows wrong line when it comes to this error in my case. It might be also in yours. Check other lines. Maybe you'll find some clues.

---

### Post by RichardCain on 2011-08-23
Thanks Birkopf, but the problem isn't with conky itself - if I put "cpu" instead it works fine - it seems to be in the way that hddtemp interacts with clock_rings.lua

It seems that hddtemp is only returning a value every few seconds

---

### Post by stinkeye on 2011-08-23
When I run hddtemp in the terminal I get
```
glen@Natty:~$ hddtemp /dev/sda
/dev/sda: WDC WD5000AAKS-22A7B0: 45°C
```

Try using 
```
hddtemp [COLOR="Red"]-n[/COLOR] /dev/sda
```

to give just a numerical output.
eg
```
glen@Natty:~$ hddtemp -n /dev/sda
45
```

**[COLOR="Red"]EDIT[/COLOR]** I now see hddtemp is also a conky variable.
Could try using the actual hddtemp program.
eg
```
${execpi 10 hddtemp -n /dev/sda}
```
in your conky instead of the conky hddtemp.


You may have to run 
```
sudo dpkg-reconfigure hddtemp
```
and answer **yes** to
> Should /usr/sbin/hddtemp be installed SUID root?
to allow hddtemp to be run as a regular user.

---

### Post by RichardCain on 2011-08-24
Thanks Stinkeye, but as I mentioned above, When I use the following in conky, everything is OK:
```
${hddtemp /dev/sda}°C
```

but when I call hddtemp in clock_rings.lua then it all goes awry; both the ring and text only read for 1 second out of 5 or 6, the text shows "N/A" the rest of the time, and the ring goes blank, taking the hands of the clock with it.

It seems that hddtemp is fine when **only** .conkyrc interrogates it, but doesn't like it when clock_rings.lua interrogates it.

clock_rings.lua only seems to accept the function
```
'hddtemp'
```
so I don't know how to route around that way

---

### Post by RichardCain on 2011-08-31
bump....


....anyone?
Is there anyone who is using hddtemp with lua?

---

### Post by stinkeye on 2011-08-31
Try posting here...
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=281865&page=1857[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=1857")
This is where all the conky eggheads hang out.

---

### Post by soneedu on 2011-09-01
```
Conky: llua_load: /root/.lua/scripts/clock_rings.lua:200: module 'cairo' not found:
   no field package.preload['cairo']
   no file './cairo.lua'
   no file '/usr/local/share/lua/5.1/cairo.lua'
   no file '/usr/local/share/lua/5.1/cairo/init.lua'
   no file '/usr/local/lib/lua/5.1/cairo.lua'
   no file '/usr/local/lib/lua/5.1/cairo/init.lua'
   no file '/usr/share/lua/5.1/cairo.lua'
   no file '/usr/share/lua/5.1/cairo/init.lua'
   no file '/usr/lib/conky/libcairo.so'
   no file './cairo.so'
   no file '/usr/local/lib/lua/5.1/cairo.so'
   no file '/usr/lib/x86_64-linux-gnu/lua/5.1/cairo.so'
   no file '/usr/lib/lua/5.1/cairo.so'
   no file '/usr/local/lib/lua/5.1/loadall.so'
Conky: desktop window (1400003) is subwindow of root window (ad)
Conky: window type - override
Conky: drawing to created window (0x2600001)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_clock_rings execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_clock_rings execution failed: attempt to call a nil value
```

```
root@debian-soneedu:~/.lua/scripts# conky -v
Conky 1.8.1 compiled Fri Aug 12 04:54:12 UTC 2011 for Linux 3.0.0-1-amd64 (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * Audacious
  * MPD
  * MOC
  * XMMS2

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * config-output
  * Imlib2
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

```

My OS:Debian
```
3.0.0-1-amd64 #1 SMP
deb http://ftp.hk.debian.org/debian/ testing main
deb-src http://ftp.hk.debian.org/debian/ testing main

```

i fixed it myself,and here is my solution:
  i check package information from [http://packages.debian.org/testing/conky](http://packages.debian.org/testing/conky) ,and i got that have conky-all pkg which archived inside contrib source, while i only added main source. that is why i cann't aptitude install conky-all.
  then i added contrib source into /etc/apt/sources.list
  and  aptitude install conky-all, will remove conky-std auto, then run conky again, will display. funny, i will try to make it nice do my best.

---

### Post by RichardCain on 2011-09-03
Thanks Stinkeye!
All sorted.

---

### Post by Calrizan on 2011-12-25
Hoorah for bumping an old thread.

This makes me feel stupid to ask, but how would I go about resolving this error?

```

onky: /root/.conkycolors/conkyrc: 9: no such configuration: 'imlib_cache_size'
Conky: unknown variable wireless_link_qual
Conky: desktop window (1000003) is subwindow of root window (103)
Conky: window type - normal
Conky: drawing to created window (0x2c00002)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_main execution failed: /usr/share/conkycolors/scripts/conkyCairo.lua:586: attempt to call global 'cairo_xlib_surface_create' (a nil value)
Conky: llua_do_call: function conky_main execution failed: /usr/share/conkycolors/scripts/conkyCairo.lua:586: attempt to call global 'cairo_xlib_surface_create' (a nil value)
Conky: llua_do_call: function conky_main execution failed: /usr/share/conkycolors/scripts/conkyCairo.lua:586: attempt to call global 'cairo_xlib_surface_create' (a nil value)
Conky: llua_do_call: function conky_main execution failed: /usr/share/conkycolors/scripts/conkyCairo.lua:586: attempt to call global 'cairo_xlib_surface_create' (a nil value)
^CConky: received SIGINT or SIGTERM to terminate. bye!

```

I have zero lua knowledge, but I intend to learn so I can see what can be done with Conky. I understand the error, but I do not know the methods to mitigate/repair said error. 

Latest source of Conky from sourceforge.
Linux Core10 2.6.32-5-686 #1 SMP Thu Nov 3 04:23:54 UTC 2011 i686 GNU/Linux

---

### Post by dk75 on 2011-12-25
I didn't investigated it much but it seems that although Conky series 2 from sourceforge compile without error then after that it won't load Imlib or Cario library from it's library directory and thus can't use cario or imlib with it.

Go to sourceforge and fill bug report to devs.

---

### Post by Calrizan on 2011-12-25
> **dk75 said:**
> I didn't investigated it much but it seems that although Conky series 2 from sourceforge compile without error then after that it won't load Imlib or Cario library from it's library directory and thus can't use cario or imlib with it.

Go to sourceforge and fill bug report to devs.

Hmm. That's mildly disappointing. I was really looking forward to a decent, scriptable monitor.

---

### Post by dk75 on 2011-12-25
Can't you use Conky 1.8.1?
It works, still...

---

### Post by Calrizan on 2011-12-25
> **dk75 said:**
> Can't you use Conky 1.8.1?
It works, still...

I suppose I could attempt to find the backports for Squeeze (assuming I do have a Squeeze install. uname -a doesn't seem to report the particular distro.)

---

### Post by akshay.chandorkar1 on 2012-01-24
Hay [stinkeye]("http://ubuntuforums.org/member.php?u=684510")....i am Akshay from india....i am trying to configure conky.....my .conkyrc says following
..................................................   ..................................................   ..................................................   ......................
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 4D6844



TEXT
 ${color D3DADF}${font OpenLogos:size=45} u t
${font weather:size=82}${color C9CFD4}${execi 600  ~/scripts/conditions.sh}${color 265276}${font}${voffset -25}  ${execi  1200 ~/scripts/pogodynka.sh}

   ${color 4EA9F3}${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${color}${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color 014A7F}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py [EMAIL="akshay.chandorkar1@gmail.com"]akshay.chandorkar1@gmail.com[/EMAIL] something 3}

   ${color 014A7F}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${color 014A7F}${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

..................................................   ..................................................   ..................................................  ...............

I got this from the website

[http://www.quicktweaks.com/2008/09/2...top/#idc-cover]("http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/#idc-cover")

and is installed as the installation giuld says
..................................................   ..................................................   ..................................................  .................

When running the conky from the terminal it says

akshay@akshay-desk:~$ conky
Conky: /home/akshay/.conkyrc: 14: no such configuration: 'border_margin'
Conky: desktop window (e00023) is subwindow of root window (b0)
Conky: window type - override
Conky: drawing to created window (0x3400001)
Conky: drawing to double buffer
/home/akshay/scripts/pogodynka.sh: 50: w3m: not found
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Traceback (most recent call last):
  File "/home/akshay/scripts/gmail_parser.py", line 46, in <module>
    f = auth()  # Do auth and then get the feed
  File "/home/akshay/scripts/gmail_parser.py", line 29, in auth
    f = opener.open(_URL)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 663, in http_error_301
    return self.http_error_302(url, fp, errcode, errmsg, headers, data)
  File "/usr/lib/python2.7/urllib.py", line 632, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 659, in redirect_internal
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 694, in http_error_401
    return getattr(self,name)(url, realm)
  File "/usr/lib/python2.7/urllib.py", line 776, in retry_https_basic_auth
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 205, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 449, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 369, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 681, in http_error_401
    errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 379, in http_error_default
    raise IOError, ('http error', errcode, errmsg, headers)
IOError: ('http error', 401, 'Unauthorized', <httplib.HTTPMessage instance at 0xb722996c>)
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
.
.
.
.

and it stops here and nothing  happens...........................................   ..................................................  .................
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11636808") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11636808")

---

### Post by dk75 on 2012-01-25
Wrong forum buddy...
You have no Cario or LUA code in your config.
Go to [Post your .conkyrc files w/ screenshots](http://ubuntuforums.org/showthread.php?t=281865) and post your code inside code tag's here.

But form my look you have old configuration (very old) with new Conky and that's why there's so much errors.
It's that what you have for using 4 years old config today.

---

### Post by Piupardo on 2012-03-05
Hi all!

I recently (today) decide to install conky from git.

Everything went well on my desktop running 11.04. Lua, Cairo, all the bindings... It is working like a charm.

Now, when I try to 'make' it on my laptop running 11.10, these message pops up:

> rui@rp-nb-ubuntu:~/conky/build$ make
[  1%] Running tolua++ on cairo.pkg
Segmentation fault
make[2]: *** [lua/libcairo-orig.c] Error 139
make[1]: *** [lua/CMakeFiles/cairo.dir/all] Error 2
make: *** [all] Error 2

EDIT:
Suddenly, with no change, it started to pass cairo and stopping in imlib2...

> rui@rp-nb-ubuntu:~/conky/build$ make
[  4%] Built target cairo
[  6%] Running tolua++ on imlib2.pkg
Segmentation fault
make[2]: *** [lua/libimlib2.c] Error 139
make[1]: *** [lua/CMakeFiles/imlib2.dir/all] Error 2
make: *** [all] Error 2



If I turn off BUILD_LUA_CAIRO and BUILD_LUA_IMLIB2 it goes well.
If I activate any of them, it gives the error.
Any ideas?

EDIT:
Can't tell you why, but it worked. I kept repeating the command until it worked!
Strange, no?

At the end, lua is not working... :(


Thanks in advance!

---

### Post by dk75 on 2012-03-05
I don't know.
Every time when I tried to build Conky2 from git I've ended up with Conky that can't do LUA at all (I mean it compiled with no errors, version check tells that it do LUA and Cairo and then it can't find lua/cairo library that it build during make).
Maybe it is problem with packaged tolua++ and we need to build it yourself in order to work.
It was with Conky 1.8 and Ubuntu 8/9 which haven't had tolua++ packaged at all ;P , so...

---

### Post by Piupardo on 2012-03-05
> Lua based configuration system [WORK IN PROGRESS]
Layout engine with cairo backend [INCOMPLETE]

Found this ^^^^
On [this page]("http://wiki.conky.be/index.php?title=Conky_2_design")

Maybe it is the answer to our questions? The reason why lua/cairo is not working well yet???....

Best regards

---

### Post by RichardCain on 2012-03-07
The *cpu* function requires an argument (i.e. *cpu0, cpu1* etc.).  This was fine on my old dual-core processor laptop, as I could just have two readouts.  However, since my new laptop has an i7 processor, it's a bit silly to have 8 different readouts.  Is there a way to average these into a single readout?

My first thought was to create a bash script to do this, but I can't find any bash commands which return cpu usage.

---

### Post by dk75 on 2012-03-07
Wrong thread.
This is for LUA and Cairo only.
You question is about core Conky function which works without any LUA or Cairo code.
Go to [Conky thread]("http://ubuntuforums.org/showthread.php?t=281865") instead.

---

### Post by RichardCain on 2012-03-08
Apologies.

Thanks for the pointer :)

---

### Post by ihatethisflavorsomuch on 2012-08-24
How the heck do I enable or download or whatever the hell I have to do in order to get lua and cairo. Its making conky ugly and I have literally been up 72 hours obsessing over this, someone just tell me how I don't want to code any scripts, or anything, I just want to install conky with the cairo/lua stuff installed. The end.

---

