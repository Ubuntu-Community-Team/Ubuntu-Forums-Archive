---
title: "Devils Pie not working"
date: 2008-12-22
forum: General Help
---

### Post by lee_connell on 2008-12-22
Can someone help me get devils pie working, i tried many examples and cannot figure out how to get it to work, doesn't seem to match any windows.  Below is code i have in my home directory under .devilspie/firefox.ds

(debug)
(if
    (is (application_name) "firefox")
    (begin
       (set_workspace 2)
       (maximize)
    )
)

---

### Post by kawaji on 2008-12-22
```
(is (application_name) "**F**irefox")
```

GUI Frontend for devilspie.
[http://code.google.com/p/gdevilspie/](http://code.google.com/p/gdevilspie/)

---

### Post by lee_connell on 2008-12-23
I've tried gdevilspie, it didn't work for me either, i'll try again and see what happens.  

thanks for reply.

---

### Post by Jose Catre-Vandis on 2008-12-23
To help you understand exactly how to label windows open a terminal and type:
```
xprop
```
Your cursor will change to a cross and use this to click on the window you want info about. Your terminal will run by plenty of information. You need to look for (for firefox):
WM_CLASS(STRING) = "Navigator", "Firefox"

and Firefox being the class name and the name you want to put in your .ds file for the application name. HTH

FWIW the code I would use to do what you want to achieve would be:

```
(if (is (application_name) "Firefox") (begin (set_workspace 2) (maximize) ) )
```
(from devilspie man, and note no use of "debug")

---

### Post by lee_connell on 2008-12-23
Thanks for reply all, it is now working, an issue I have found is that it doesn't seem to center anything, which is what i have for an action for my text editor:

; generated_rule gedit
( if 
( and 
( is ( application_name ) "Text Editor" )
) 
( begin 
( center )
( println "match" )
)
)

it prints the match but does not center the window. centering windows and geometry is going to be my main use of devilspie if it works.

thanks!

---

### Post by kawaji on 2008-12-23
> (from devilspie man, and note no use of "debug")

That would be a solution. :KS

P.S.
If Compiz is running, using "set_viewport" instead of "set_workspace" is needed.

EDIT:
oh ... 1 minuite late

---

### Post by kawaji on 2008-12-23
@lee_connell

Window selecter of Gdevilspie seemes to get wrong name.
xprop command would be more reliable.
I think ( is ( window_class ) "Gedit" ) would make your rule work.
(but "center" action does not work on desktop running compiz, though..)

---

### Post by lee_connell on 2008-12-23
Then compiz is what what the problem is then :)

does compiz have the ability to use regex and position windows?

---

### Post by kawaji on 2008-12-23
> Viewports and desktops are not the same concept. For technical reasons, changing the number of "desktops" or "workspaces" in environments such as GNOME, KDE, and Xfce is not the same as changing the number of viewports in Compiz.

Viewports is like parts of single big desktop.

I think that's why some rules of devilspie do not work correctly on compiz.

---

### Post by Jose Catre-Vandis on 2008-12-23
> **lee_connell said:**
> Then compiz is what what the problem is then :)

does compiz have the ability to use regex and position windows?

Yes, use compiz window matching rules to achieve the same

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

---

### Post by lee_connell on 2008-12-24
Jose,

Compiz is doing all the stuff I want it to do, thanks!

one issue, which i did already post about is i want "window rules" to run before "window placement" plugin, how is this done, i can't find info on it.

---

