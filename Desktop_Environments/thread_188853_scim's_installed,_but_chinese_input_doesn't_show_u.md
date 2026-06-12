---
title: "scim's installed, but chinese input doesn't show up in options"
date: 2006-06-04
forum: Desktop Environments
---

### Post by gemgem on 2006-06-04
hi, i just installed Dapper. I would like to be able to input traditional chinese text (zh-tw) and I followed the steps outlined here: [https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake](https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake)
but i still can't get scim to show up with a chinese input option.

i am currently using an english language locale, and would like to keep it that way, but i would like to be able to input traditional chinese text. according to the help sites i checked out, "scim-chewing" is supposed to be installed to be able to type traditional chinese. _i checked out synaptic, and "scim-chewing" IS installed_, so i don't know why whenever i turn on scim, only "english/ european" shows up. the only other input option is "raw code".

[U]
i tried logging in using a chinese (taiwan) locale, but scim still only shows "english/european" and "raw code" (i dont know what that is) as input options. no traditional chinese.[/U]

i followed step #2 of [https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake](https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake)
but if you look at the picture
[IMG]https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake?action=AttachFile&do=get&target=Screenshot-Language_Support.png[/IMG]
it says to tick the box beside Chinese right? 
_i ticked it, but i could only get the box to show a little horizontal line. if i clicked again, a check shows up **(like in the picture)**, but after i click "apply", a dialog box will say something about how some translations/languages aren't fully supported_ (i can't remember the exact text).

in the second part (Additional configuration if you're not using a CJK session) of the [wiki page]("https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake"), it says to type ```
im-switch -z &#8220;your locale&#8221; -s scim
``` in terminal. so i did, i typed ```
im-switch -z zh_tw -s scim
```. but then terminal replies with 
_"bash: im-switch command not found" or "bash: im-switch command doesn't exist"_ (something like that).

in the third part (where it says In case all of this doesn't work), [the wiki page]("https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake") suggests opening ```
gedit ~/.scim/global
```  and adding ```
/SupportedUnicodeLocales = en_US.UTF-8,zh_TW.UTF-8 
```to the file and saving it. but it still doesn't work.

i logged out and logged in after trying each of these steps, but still no go.

could someone help me out? _i would like to keep english as my locale, but i would like to be able to input traditional characters_. 

_i would also like scim input to be the default input method_ how do i do this?. for example, when i was trying to see if i could type in chinese, i had to right click and select "SCIM" out of a long list of "input with..." options in gedit. and then after SCIM's open, there's only "english/ european" as an input option.

---

### Post by rbalfour on 2006-06-04
I use Japanese in English Desktop.
Try this command instead.
> im-switch -s scim_xim -z default

This is what worked for me.

---

### Post by gemgem on 2006-06-05
hi rbalfour,

i tried "im-switch -s scim_xim -z default" and just like when i typed "im-switch -z zh_tw -s scim" as i said in my first message, terminal says "bash: im-switch command not found".

---

### Post by dakuran on 2007-09-17
Hi guys, I've fully installed Japanese text support, and since scim was packaged nicely w/feisty, I've only had to do some minor tweaking, I can start up feisty in japanese and all the rest, however, my problem is that when i email in japanese to my friends, they get nothing but jiberish, this has happened w/two different friends (an XP usr and a Vista usr) my email addy is from hotmail, I'm just wondering if i perhaps forgot to install something or maybe hotmail, just doesn't like when I type in japanese in feisty, when i was using XP i didn't have this problem so I kind of think its Feisty, but any tips/advice is greatly appreciated!

---

