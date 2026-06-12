---
title: "xbindkeys config?"
date: 2009-03-19
forum: Desktop Environments
---

### Post by tossable001 on 2009-03-19
I'm getting this error:

```
admn@mobile1:~$ xbindkeys_show 
Error in startup script: "/home/admn/.mutt.sh&"
    Control+Alt + m
Warning: unkown key in RC file : /home/admn/.xbindkeysrc
    while executing
"exec "xbindkeys" "--show" "
    invoked from within
"if { $arg1 != "" && $file_option != "" } {
        set list [ exec "xbindkeys" "--show" "$file_option" "$arg1" ]
    } else {
        set list [ exec "xbindkeys" "-..."
    (file "/usr/bin/xbindkeys_show" line 45)
```

From this config, the line 45 is the "control + alt + m"

```
################
## My config
################
#luanch mutt in an xterm with either ctrl + alt + m
"/home/admn/.mutt.sh&"
        control + alt + m
#luanch an xterm
"xterm -rv -geometry 80x23&"
        control + alt + enter
#luanch firefox
"firefox %u&"
        control + alt + i
#launch konqurer
"kfmclient openProfile webbrowsing&"
        control + alt + k
##################################
# End of xbindkeys configuration #
##################################
```


The thing that has me confused is the first entry works fine, none of the others do though. Any ideas?

Thanks

Gabe

---

