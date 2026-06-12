---
title: "can't use scim in English system"
date: 2006-10-27
forum: Desktop Environments
---

### Post by yuliang on 2006-10-27
I installed Chinese Language support from System -> Language Support. Then I got SCIM, but i can't use it unless I choose the default language to be Chinese and relogin. Is this a problem of SCIM or does it just works like that?

---

### Post by mgaleano on 2006-10-28
Hello 

I have the same problem as well. But I can tell you the SCIM works in some programs and not others. Open Gedit and right click on the text area and select the input method. 

The thing I would like to know if you can use this method with a web browser. I type my chinese mostly in email. Its a bit of a pain to cut and paste using gmail. 

Thanks
Matt

---

### Post by ZeeG on 2006-10-29
> **mgaleano said:**
> Hello 

I have the same problem as well. But I can tell you the SCIM works in some programs and not others. Open Gedit and right click on the text area and select the input method. 

The thing I would like to know if you can use this method with a web browser. I type my chinese mostly in email. Its a bit of a pain to cut and paste using gmail. 

Thanks
Matt
Are you using edgy? 
I had exactly the same problem with yuliang. 
It was OK with dapper, but after installing the edgy version, I have this issue.

---

### Post by Ironfrost on 2006-10-30
I was having the same problem, but the instructions at [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM) helped me to sort it out. See the heading “Additionnal configuration if you're not using a CJK session“ - basically you have to use im-switch to tell the system to always use SCIM.

---

### Post by ZeeG on 2006-10-30
> **Ironfrost said:**
> I was having the same problem, but the instructions at [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM) helped me to sort it out. See the heading “Additionnal configuration if you're not using a CJK session“ - basically you have to use im-switch to tell the system to always use SCIM.
Thanks, it works like a charm :)
However, I have small problem.
Whenever I log in, I'm getting error message saying "scim-launcher" closed unexpectedly.
After closing the error dialog box, I'm able to use SCIM, though.
Any thought on this?

---

### Post by zanglang on 2006-11-01
ZeeG:
Just found out that once you've the 'im-switch' command according to the wiki you'll no longer need to start 'scim -d' manually in .xsession (or System -> Preferences -> Sessions, whichever you've used) for SCIM to work. Try disabling/removing it? :)

---

