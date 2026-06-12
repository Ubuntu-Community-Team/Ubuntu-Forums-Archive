---
title: "Conky rss not behaving"
date: 2009-06-03
forum: General Help
---

### Post by m00se3724 on 2009-06-03
My Conky RSS script works on my macbook pro, but on my desktop computer it shows up for a split second then all turns white. I'm not sure why, here's the script:

own_window_title conkyrss

max_user_text 20000

use_xft yes
xftfont DejaVu Sans:size=7
override_utf8_locale yes
xftalpha 1

update_interval 1
draw_shades no
default_shade_color 2525ff
draw_outline no
default_outline_color 2525ff
draw_borders no
stippled_borders no
border_margin 0
border_width 1

no_buffers yes
uppercase no
double_buffer yes
use_spacer none

default_color ffffff
color0 ffffff
color1 cfdfdf
color2 bfbfbf
color3 0a0a0a #111111 #1a1a1a #720000
color4 080808 #101010

own_window yes
own_window_colour 080808
own_window_transparent no
own_window_type dock
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
background yes
alignment bottom_left
gap_x -2
gap_y 50
minimum_size 1440 0

TEXT
${voffset -3}
${voffset -5}${font Liberation Sans:size=8}${color}${goto 20}CNN | World${voffset -1}${goto 84}${font conkydings:size=12}${color FFA043}C${voffset -3}${goto 225}${font Liberation Sans:size=8}${color}CNN | US${voffset -1}${goto 277}${font conkydings:size=12}${color FFA043}C${voffset -3}${goto 420}${font Liberation Sans:size=8}${color}ABC News | World${voffset -1}${goto 512}${font conkydings:size=12}${color FFA043}C${voffset -3}${goto 627}${font Liberation Sans:size=8}${color}ABC News | US${voffset -1}${goto 707}${font conkydings:size=12}${color FFA043}C${voffset -3}${goto 835}${font Liberation Sans:size=8}${color}BBC News | World${voffset -1}${goto 928}${font conkydings:size=12}${color FFA043}C${voffset -3}${goto 1010}${font Liberation Sans:size=8}${color}Wired | Top Stories${voffset -1}${goto 1106}${font conkydings:size=12}${color FFA043}C${voffset -3}${goto 1222}${font Liberation Sans:size=8}${color}Slashdot | Geek${voffset -1}${goto 1300}${font conkydings:size=12}${color FFA043}C${voffset -3}${font}${color1}

${voffset -1}${goto 20}${rss [http://rss.cnn.com/rss/cnn_world.rss](http://rss.cnn.com/rss/cnn_world.rss) 30 item_title 0}${goto 210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 225}${rss [http://rss.cnn.com/rss/cnn_us.rss](http://rss.cnn.com/rss/cnn_us.rss) 30 item_title 0}${goto 410}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 420}${rss [http://www.abc.net.au/news/indexes/world/rss.xml](http://www.abc.net.au/news/indexes/world/rss.xml) 30 item_title 0}${goto 610}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 627}${rss [http://feedproxy.google.com/AbcNews_US](http://feedproxy.google.com/AbcNews_US) 30 item_title 0}${goto 810}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 835}${rss [http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml](http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml) 30 item_title 0}${goto 1010}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1010}${rss [http://feeds.wired.com/wired/index](http://feeds.wired.com/wired/index) 30 item_title 0}${goto 1210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1222}${rss [http://rss.slashdot.org/Slashdot/slashdot](http://rss.slashdot.org/Slashdot/slashdot) 30 item_title 0}${goto 1420}${color4}${fs_bar 10,100 /fakelol/}${color1}
${voffset -1}${goto 20}${rss [http://rss.cnn.com/rss/cnn_world.rss](http://rss.cnn.com/rss/cnn_world.rss) 30 item_title 1}${goto 210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 225}${rss [http://rss.cnn.com/rss/cnn_us.rss](http://rss.cnn.com/rss/cnn_us.rss) 30 item_title 1}${goto 410}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 420}${rss [http://www.abc.net.au/news/indexes/world/rss.xml](http://www.abc.net.au/news/indexes/world/rss.xml) 30 item_title 1}${goto 610}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 627}${rss [http://feedproxy.google.com/AbcNews_US](http://feedproxy.google.com/AbcNews_US) 30 item_title 1}${goto 810}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 835}${rss [http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml](http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml) 30 item_title 1}${goto 1010}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1010}${rss [http://feeds.wired.com/wired/index](http://feeds.wired.com/wired/index) 30 item_title 1}${goto 1210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1222}${rss [http://rss.slashdot.org/Slashdot/slashdot](http://rss.slashdot.org/Slashdot/slashdot) 30 item_title 1}${goto 1420}${color4}${fs_bar 10,100 /fakelol/}${color1}
${voffset -1}${goto 20}${rss [http://rss.cnn.com/rss/cnn_world.rss](http://rss.cnn.com/rss/cnn_world.rss) 30 item_title 2}${goto 210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 225}${rss [http://rss.cnn.com/rss/cnn_us.rss](http://rss.cnn.com/rss/cnn_us.rss) 30 item_title 2}${goto 410}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 420}${rss [http://www.abc.net.au/news/indexes/world/rss.xml](http://www.abc.net.au/news/indexes/world/rss.xml) 30 item_title 2}${goto 610}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 627}${rss [http://feedproxy.google.com/AbcNews_US](http://feedproxy.google.com/AbcNews_US) 30 item_title 2}${goto 810}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 835}${rss [http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml](http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml) 30 item_title 2}${goto 1010}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1010}${rss [http://feeds.wired.com/wired/index](http://feeds.wired.com/wired/index) 30 item_title 2}${goto 1210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1222}${rss [http://rss.slashdot.org/Slashdot/slashdot](http://rss.slashdot.org/Slashdot/slashdot) 30 item_title 2}${goto 1420}${color4}${fs_bar 10,100 /fakelol/}${color1}
${voffset -1}${goto 20}${rss [http://rss.cnn.com/rss/cnn_world.rss](http://rss.cnn.com/rss/cnn_world.rss) 30 item_title 3}${goto 210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 225}${rss [http://rss.cnn.com/rss/cnn_us.rss](http://rss.cnn.com/rss/cnn_us.rss) 30 item_title 3}${goto 410}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 420}${rss [http://www.abc.net.au/news/indexes/world/rss.xml](http://www.abc.net.au/news/indexes/world/rss.xml) 30 item_title 3}${goto 610}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 627}${rss [http://feedproxy.google.com/AbcNews_US](http://feedproxy.google.com/AbcNews_US) 30 item_title 3}${goto 810}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 835}${rss [http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml](http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml) 30 item_title 3}${goto 1010}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1010}${rss [http://feeds.wired.com/wired/index](http://feeds.wired.com/wired/index) 30 item_title 3}${goto 1210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1222}${rss [http://rss.slashdot.org/Slashdot/slashdot](http://rss.slashdot.org/Slashdot/slashdot) 30 item_title 3}${goto 1420}${color4}${fs_bar 10,100 /fakelol/}${color1}
${voffset -1}${goto 20}${rss [http://rss.cnn.com/rss/cnn_world.rss](http://rss.cnn.com/rss/cnn_world.rss) 30 item_title 4}${goto 210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 225}${rss [http://rss.cnn.com/rss/cnn_us.rss](http://rss.cnn.com/rss/cnn_us.rss) 30 item_title 4}${goto 410}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 420}${rss [http://www.abc.net.au/news/indexes/world/rss.xml](http://www.abc.net.au/news/indexes/world/rss.xml) 30 item_title 4}${goto 610}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 627}${rss [http://feedproxy.google.com/AbcNews_US](http://feedproxy.google.com/AbcNews_US) 30 item_title 4}${goto 810}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 835}${rss [http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml](http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml) 30 item_title 4}${goto 1010}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1010}${rss [http://feeds.wired.com/wired/index](http://feeds.wired.com/wired/index) 30 item_title 4}${goto 1210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1222}${rss [http://rss.slashdot.org/Slashdot/slashdot](http://rss.slashdot.org/Slashdot/slashdot) 30 item_title 4}${goto 1420}${color4}${fs_bar 10,100 /fakelol/}${color1}${voffset -1}

Anyone have any ideas as to why this is happening?

---

