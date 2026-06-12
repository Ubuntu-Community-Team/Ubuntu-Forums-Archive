---
title: "Can't switch keyboard layout, Global shortcuts don't work"
date: 2009-06-04
forum: Desktop Environments
---

### Post by jackhab on 2009-06-04
Hi,
I have a problem with my Kubuntu Jauty. Every time I reboot the global shortcuts stop working. When I check Global Keyboard Shortcuts in System Settings I can see all my system and custom shortcuts assigned properly. But only after I delete and reassign each (!) shortcut it starts working (even the basic ones like Alt-Tab).

I also have a problem with keyboard layout switching. Not sure if it's related to the above problem. When I switch layout it always types in English regardless the language shown by the keyboard layout indicator.

There is a command field in the Keyboard Layout dialog showing the following command ```
setxkbmap -model pc104 -layout us,il -variant ,
```
When I try to run this command in terminal it gives ```
Error loading new keyboard description
```

Please, help.

---

### Post by longmatys on 2009-06-23
I have the same issue but for that command:

setxkbmap -model pc104 -layout us,cz -variant qwerty_bksl,qwerty_bksl

For me it is problem with us keyboard, if you select it, it will add that option qwerty_bksl. So twice that option results in error. Also if I chose standard us layout it place them "-variant  " so it also result in error. If I chose option with Euro sign it is ok...:P

---

### Post by longmatys on 2009-06-23
> **jackhab said:**
> Hi,
I have a problem with my Kubuntu Jauty. Every time I reboot the global shortcuts stop working. When I check Global Keyboard Shortcuts in System Settings I can see all my system and custom shortcuts assigned properly. But only after I delete and reassign each (!) shortcut it starts working (even the basic ones like Alt-Tab).

I also have a problem with keyboard layout switching. Not sure if it's related to the above problem. When I switch layout it always types in English regardless the language shown by the keyboard layout indicator.

There is a command field in the Keyboard Layout dialog showing the following command ```
setxkbmap -model pc104 -layout us,il -variant ,
```
When I try to run this command in terminal it gives ```
Error loading new keyboard description
```


Please, help.

If you select different us keyboard (for example with euro sign) it will be ok! It worked for me.

---

