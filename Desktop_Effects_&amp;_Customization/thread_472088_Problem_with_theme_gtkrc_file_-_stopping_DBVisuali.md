---
title: "Problem with theme gtkrc file - stopping DBVisualizer"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by leepr on 2007-06-12
Hi there,

I'm trying to run the installation file for  [DBVisualizer]("http://www.minq.se/products/dbvis/index.html"), but it displays an *empty* window with the title, "Setup - DBVisualizer 5.1.1", and gives the following error message in the terminal:

```
lee@lee:~/Applications$ ./dbvis_linux_5_1_1.sh 
Starting Installer ...
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:34: error: lexical error or unexpected token, expected valid token
```

Line 34 of that file contains the following:

```
  fg[NORMAL]        = @fg_color #"#000000" # black
```

When I change it to the following, it has a problem with the next line:

```
  fg[NORMAL]        = "#000000" # black
```

When I go through the whole file and delete all @<VARIABLE> references, it just displays a blank window. 

Can anyone tell me what the problem may be, or how I can work around it? I tried changing my window themes, but I get the same error for them (just a different file name and line number).

Thanks in advance for your thoughts.

 - LeePR

---

