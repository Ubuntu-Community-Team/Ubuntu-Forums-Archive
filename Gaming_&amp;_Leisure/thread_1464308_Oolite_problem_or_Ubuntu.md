---
title: "Oolite problem or Ubuntu"
date: 2010-04-28
forum: Gaming &amp; Leisure
---

### Post by Rustybolts on 2010-04-28
Oolite 1.73.4 
Ubuntu 9.10 Acer 5332 Laptop 
 
Unable to use certain keys to play game when i remap keyconfig.plist for example 
TAB key - energy bomb have to remap 
# key - wont function 
/ key -wont function 
haven't tested following keys but assume will have similar problems 
~ @ ' : ; ? > < , . + - { } [ ] \ |

Not much luck on Oolite forum so far so thought i would post here, in case it is Ubuntu problem.

---

### Post by mastablasta on 2010-04-28
Unfortunatelly i just packed my linux computer for transport. can you tell me what the "# key" actually does? Why the keys won't function? How does that look like? they just don't react or do something else or what?
 
As i know Oolite sues mostly keys on the main keyboard and a couple from numeric keyboard on the right. Tab could be an issue since it's a usefull device that it connects to.
 
Is it not possible to remap these keys to some letter key? i am sure there are a few still not assigned. or maybe i am just not using them.

---

### Post by Rustybolts on 2010-04-28
I have changed many of the keys myself with an oxp i created a couple of years ago from my windows days, so there is nothing wrong with the oxp itself as it has been tested.
The tab key is used in original key layout which does not respond on my linux install. The other keys i mentioned "#" is to change advanced compass setting which Oolite on my linux install no longer reacts to the key being pressed.

Yes they can be remapped to other letters but they are not always in the ideal locations if you are limited to using 2/3 of your keyboard.

Below is my code from my keyconfig.plist

code:
> {
    key_roll_left                = 253;        // left arrow
    key_roll_right                = 252;        // right arrow
    key_pitch_forward            = 255;        // up arrow
    key_pitch_back                = 254;        // down arrow
    key_yaw_left                = "a";
    key_yaw_right                = "d";

    key_increase_speed            = "w";
    key_decrease_speed            = "s";
    key_inject_fuel                = "x";

    key_fire_lasers                = "q";
    key_launch_missile            = "m";
    key_next_missile            = "y";
    key_ecm                    = "e";

    key_target_missile            = "t";
    key_untarget_missile            = "u";
    key_ident_system            = "r";

    key_scanner_zoom            = "z";
    key_scanner_unzoom            = "Z";

    key_launch_escapepod            = 27;        // escape
    key_energy_bomb                = "\t";        // tab

    key_galactic_hyperspace            = "g";
    key_hyperspace                = "h";
    key_jumpdrive                = "j";

    key_dump_cargo                = "/";
    key_rotate_cargo            = "R";

    key_autopilot                = "n";
    key_autopilot_target            = "N";
    key_autodock                = "l";
    key_docking_clearance_request        = "L";

    key_snapshot                = "*";
    key_docking_music            = "s";

    key_advanced_nav_array            = "^";
    key_map_home                = 302;        // Home
    key_map_info                = "i";

    key_pausebutton                = "p";
    key_show_fps                = "F";
    key_mouse_control            = "M";

    key_comms_log                = "`";
    key_next_compass_mode            = "#";
    
    key_cloaking_device            = "0";

    key_contract_info            = "?";

    key_next_target                = "+";
    key_previous_target            = "-";

    key_custom_view                = "v";

    key_dump_target_state            = "H";
}

---

### Post by mastablasta on 2010-04-29
I don't really know how to solve your problem (i play it in winXP), but can i suggest moving keys that are not essential to the right side of the keyboard and then replacing that part with essential keys. For example those for docking are not really of high imporatnce, since usually you have time to use them. so i think you could either move them to numlock or to those insert, home etc. ones. that would free up space on the left side of keyboard to put keys for compass and such. as well as for the energy bomb. maybe space could be used for energy bomb or somehting.
 
i am just using default config. I don't really use advanced compass for example. i don't know what good it is since there is always one planet and one sun and station is always near planet and usually clearly visible. anyway the default keys are fine with me but if i wanted to put the energy bomb elsewhere i would choose q, which you already have for fire...
 
Haven't figured out where to get the cloaking device...

---

### Post by Rustybolts on 2010-04-29
> **mastablasta said:**
> I don't really know how to solve your problem (i play it in winXP), but can i suggest moving keys that are not essential to the right side of the keyboard and then replacing that part with essential keys. For example those for docking are not really of high imporatnce, since usually you have time to use them. so i think you could either move them to numlock or to those insert, home etc. ones. that would free up space on the left side of keyboard to put keys for compass and such. as well as for the energy bomb. maybe space could be used for energy bomb or somehting.
 
i am just using default config. I don't really use advanced compass for example. i don't know what good it is since there is always one planet and one sun and station is always near planet and usually clearly visible. anyway the default keys are fine with me but if i wanted to put the energy bomb elsewhere i would choose q, which you already have for fire...
 
Haven't figured out where to get the cloaking device...
Sounds to  me like you haven't installed any addons extra ships, more missions, Hoopy casino, Con stores, Space bars, Prison stations, More than one planet and moons in given areas. Then your space compass becomes a bit more important. To download addons you may find [COLOR=Red]>>[/COLOR][THIS]("http://wiki.alioth.net/index.php/OXP")[COLOR=Red]<<[/COLOR]page helpfull, or [COLOR=Red]>>[/COLOR][HERE]("http://www.mediafire.com/?sharekey=ca166c7e38ef78c6e7c82ed4b8f0c380e04e75f6e8ebb871")[COLOR=Red]<<[/COLOR] to download some that i created (hyperradiost01 , hyperradiost02 are music packs for Hyperradio addon that someone else created).
As far as my problem with the keys i have now got some feed back on Oolite forum from some of the developers and they are looking into it.

Regarding cloaking device below excerpt from Oolite wiki
> 
**  SPOILER ALERT ------- SPOILER ALERT **

 Highlight the paragraph below to read. [COLOR=white]The cloaking device mission is informal in the sense you do not get a display screen. On roughly your sixth jump through the 5th galaxy, you shall arrive to meet normally 3 happy vessels. Suddenly, 1 shall fire one you whilst the other just sits there idly. The one that fires on you then turns away - still orange. You could kill them, but better is to wonder where the third ship went? They will start firing on you soon and will flicker visibly, but not on radar. They will be untargetable. Kill them carefully and pick up the cargo. You then have the cloaking device. WARNING - IF YOU MISS THIS MISSION (DEATH, DESTRUCTION OF DEVICE, THEY GOT AWAY) YOU MUST LOAD THE GAME AND TRY AGAIN. THE MISSION DOES NOT COME TWICE![/COLOR] 


---

