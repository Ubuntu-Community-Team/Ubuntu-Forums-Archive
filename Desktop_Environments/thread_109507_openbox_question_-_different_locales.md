---
title: "openbox question - different locales"
date: 2005-12-28
forum: Desktop Environments
---

### Post by yohan on 2005-12-28
I have a question about executing a command in either the menu or with a shortcut. 

A post in the menu.xml is for example:
        <item label="aterm"> <action name="Execute">
                <execute>aterm</execute>
            </action> </item>
This works and aterm is opened. My problem is that I would like to open aterm with a swedish locale instead. From the console I could write this:
LC_CTYPE="sv_SE" aterm
But if I try this as a menu post:
        <item label="aterm"> <action name="Execute">
                <execute>LC_CTYPE="sv_SE" aterm</execute>
            </action> </item>
It doesnt work!

Why? I guess openbox has to open shellscripts or whatever. Can someone help me how to make a shellscript to specify which locale to execute a program with? Is it possible?

Thanks!

Johan

---

