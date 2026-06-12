---
title: "Post your .awesomerc configs"
date: 2008-04-15
forum: Desktop Environments
---

### Post by MediaMike on 2008-04-15
I recently started tinkering with the Awesome WM and haven't found any threads on any forums I frequent showing off individuals .awesomerc configs and what they installed or had to configure to get their config working.  I would post mine but it extremely basic other than renaming the tags and changing some of the keys.

Post a screenshot of it in action too.

---

### Post by dbbolton on 2008-06-03
I just installed awesome today.  My setup is pretty much default:

```

 screen 0
 {
     styles
     {
         normal
         {
             font = "nu"
             fg = "#ffffff"
             bg = "#000000"
             border = "#1a1a1a"
         }
         focus
         {
             fg = "#ff8800"
             bg = "#000000"
             border = "#ffffff"
         }
         urgent
         {
             fg = "#6FCE07"
             bg = "#1a1a1a"
         }
      }
     tags
     {
         tag 1 { }
         tag 2 { }
         tag 3 { }
         tag 4 { }
     }
     layouts
     {
         layout tile { image = "/usr/local/share/awesome/icons/layouts/tilew.png" }
         layout tileleft { image = "/usr/local/share/awesome/icons/layouts/tileleftw.png" }
         layout tilebottom { image = "/usr/local/share/awesome/icons/layouts/tilebottomw.png" }
         layout tiletop { image = "/usr/local/share/awesome/icons/layouts/tiletopw.png" }
         layout max { image = "/usr/local/share/awesome/icons/layouts/maxw.png" }
         layout spiral { image = "/usr/local/share/awesome/icons/layouts/spiralw.png" }
         layout dwindle { image = "/usr/local/share/awesome/icons/layouts/dwindlew.png" }
         layout floating { image = "/usr/local/share/awesome/icons/layouts/floatingw.png" }
     }
     statusbar mystatusbar
     {
         position = "top"
         taglist mytaglist
         {
             mouse
             {
                 button = "1"
                 command = "tag_view"
             }
             mouse
             {
                 button = "1"
                 modkey = {"Mod4"}
                 command = "client_tag"
             }
             mouse
             {
                 button = "3"
                 command = "tag_toggleview"
             }
             mouse
             {
                 button = "3"
                 modkey = {"Mod4"}
                 command = "client_toggletag"
             }
             mouse
             {
                 button = "4"
                 command = "tag_viewnext"
             }
             mouse
             {
                 button = "5"
                 command = "tag_viewprev"
             }
         }
         layoutinfo mylayoutinfo
         {
             mouse
             {
                 button = "1"
                 command = "tag_setlayout"
                 arg = "+1"
             }
             mouse
             {
                 button = "4"
                 command = "tag_setlayout"
                 arg = "+1"
             }
             mouse
             {
                 button = "3"
                 command = "tag_setlayout"
                 arg = "-1"
             }
             mouse
             {
                 button = "5"
                 command = "tag_setlayout"
                 arg = "-1"
             }
         }
         #tasklist
         iconbox logo
         {
	     align = "right"
             image = "/home/daniel/Art/awesome16.png"
             mouse
             {
                 button = "1"
                 command = "spawn"
                 arg = "exec xterm -e man awesome"
             }
         }
     }
 }
 rules
 {
     rule { name = "Gimp" float = true }
     rule { name = "MPlayer" float = true }
     rule { name = "Acroread" float = true }
     rule { name = "pinentry" float = true }
 }
 mouse
 {
     root
     {
         button = "3"
         command = "spawn"
         arg = "exec xterm"
     }
     root
     {
         button = "5"
         command = "tag_viewnext"
     }
     root
     {
         button = "4"
         command = "tag_viewprev"
     }
     client
     {
         modkey = {"Mod4"}
         button = "1"
         command = "client_movemouse"
     }
     client
     {
         modkey = {"Mod4"}
         button = "2"
         command = "client_zoom"
     }
     client
     {
         modkey = {"Mod4"}
         button = "3"
         command = "client_resizemouse"
     }
     titlebar
     {
         button = "1"
         command = "client_movemouse"
     }
     titlebar
     {
         button = "3"
         command = "client_resizemouse"
     }
 }
 keys
 {
     key
     {
         modkey = {"Mod4"}
         key = "F1"
         command = "spawn"
         arg = "for i in /usr/share/man/man?;do ls $i; done | cut -d. -f1 | awesome-menu -e 'xterm -e man ' 'See manual page for:'"
     }
     key
     {
         modkey = {"Mod4"}
         key = "F2"
         command = "spawn"
         arg = "find /usr/bin -type f -executable ! -empty | awesome-menu -e 'exec ' Execute:"
     }
     key
     {
         modkey = {"Mod4"}
         key = "F3"
         command = "spawn"
         arg = "cut -d' ' -f1 ~/.ssh/known_hosts | cut -d, -f1 | awesome-menu -e 'xterm -e ssh ' 'ssh to:'"
     }
     key
     {
         modkey = {"Mod4"}
         key = "Return"
         command = "spawn"
         arg = "exec xterm"
     }
     key
     {
         modkey = {"Mod4"}
         key = "space"
         command = "tag_setlayout"
         arg = "+1"
     }
     key
     {
         modkey = {"Mod4", "Shift"}
         key = "space"
         command = "tag_setlayout"
         arg = "-1"
     }
     key
     {
         modkey = {"Mod4"}
         key = "b"
         command = "statusbar_toggle"
     }
     key
     {
         modkey = {"Mod4"}
         key = "j"
         command = "client_focusnext"
     }
     key
     {
         modkey = {"Mod4"}
         key = "k"
         command = "client_focusprev"
     }
     key
     {
         modkey = {"Mod4"}
         key = "Tab"
         command = "focus_history"
         arg = "-1"
     }
     key
     {
         modkey = {"Mod4", "Shift"}
         key = "j"
         command = "client_swapnext"
     }
     key
     {
         modkey = {"Mod4", "Shift"}
         key = "k"
         command = "client_swapprev"
     }
     key
     {
         modkey = {"Mod4", "Control"}
         key = "j"
         command = "screen_focus"
         arg = "+1"
     }
     key
     {
         modkey = {"Mod4", "Control"}
         key = "k"
         command = "screen_focus"
         arg = "-1"
     }
     key
     {
         modkey = {"Mod4"}
         key = "h"
         command = "tag_setmwfact"
         arg = "-0.05"
     }
     key
     {
         modkey = {"Mod4"}
         key = "l"
         command = "tag_setmwfact"
         arg = "+0.05"
     }
     key
     {
         modkey = {"Mod4", "Shift"}
         key = "h"
         command = "tag_setnmaster"
         arg = "+1"
     }
     key
     {
         modkey = {"Mod4", "Shift"}
         key = "l"
         command = "tag_setnmaster"
         arg = "-1"
     }
     key
     {
         modkey = {"Mod4", "Control"}
         key = "h"
         command = "tag_setncol"
         arg = "+1"
     }
     key
     {
         modkey = {"Mod4", "Control"}
         key = "l"
         command = "tag_setncol"
         arg = "-1"
     }
     key
     {
         modkey = {"Mod4"}
         key = "Escape"
         command = "tag_prev_selected"
     }
     key
     {
         modkey = {"Mod4"}
         key = "Left"
         command = "tag_viewprev"
     }
     key
     {
         modkey = {"Mod4"}
         key = "Right"
         command = "tag_viewnext"
     }
     key
     {
         modkey = {"Mod4"}
         key = "m"
         command = "client_togglemax"
     }
     key
     {
         modkey = {"Mod4", "Control"}
         key = "Return"
         command = "client_zoom"
     }
     key
     {
         modkey = {"Mod4", "Control"}
         key = "space"
         command = "client_togglefloating"
     }
     key
     {
         modkey = {"Mod4"}
         key = "s"
         command = "client_togglescratch"
     }
     key
     {
         modkey = {"Mod4", "Control"}
         key = "s"
         command = "client_setscratch"
     }
     key
     {
         modkey = {"Mod4", "Shift"}
         key = "c"
         command = "client_kill"
     }
     key
     {
         modkey = {"Mod4", "Shift"}
         key = "q"
         command = "quit"
     }
     key
     {
         modkey = {"Mod4", "Control"}
         key = "r"
         command = "restart"
     }
     key
     {
        modkey = {"Mod4"}
        key = "0"
        command = "tag_view"
     }
     keylist
     {
         modkey = {"Mod4"}
         command = "tag_view"
         keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
         arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
     }
     key
     {
         modkey = {"Mod4", "Control"}
         key = "0"
         command = "tag_toggleview"
     }
     keylist
     {
         modkey = {"Mod4", "Control"}
         command = "tag_toggleview"
         keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
         arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
     }

     key
     {
         modkey = {"Mod4", "Shift"}
         key = "0"
         command = "client_tag"
     }
     keylist
     {
         modkey = {"Mod4", "Shift"}
         command = "client_tag"
         keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
         arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
     }

     key
     {
         modkey = {"Mod4", "Shift", "Control"}
         key = "0"
         command = "client_toggletag"
     }

     key 
     { 
         modkey = {"Mod4"} 
         key = "p" 
         command = "spawn" 
         arg = "exec `cat ~/.awesome/menu | awesome-menu 'Run:'`" 
     }

     keylist
     {
         modkey = {"Mod4", "Shift", "Control"}
         command = "client_toggletag"
         keylist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
         arglist = { 1, 2, 3, 4, 5, 6, 7, 8, 9 }
     }
 }
 # vim: filetype=conf

```

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/sshot/th_2008-06-03-172452_1024x768_scrot.png[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/sshot/2008-06-03-172452_1024x768_scrot.png)

Does anyone know how to disable images in the awesome tasklist?

---

### Post by Nythain on 2008-06-14
not sure if you've figured it out yet, but in your tasklist section you can add
show_icons = "false"

and im saddend by the lack of awesomerc's posted so far :(

---

