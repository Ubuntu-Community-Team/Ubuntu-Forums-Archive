---
title: "Opera - upgrade?"
date: 2008-12-17
forum: General Help
---

### Post by JimTDI on 2008-12-17
Maybe one of you more experienced Opera users can help answer a question for me.

I see there is now an update to 9.63 Opera.  I have 9.62 installed.  I know how to upgrade on Windoze - but in Ubuntu, how do I upgrade Opera?

If I download the .deb file for 9.63, will it upgrade my existing Opera install, or do I somehow need to remove the prior installed Opera (seems like quite a job, cause there's ALOT of files it installed), and then install the new .deb file ??

Thanks for any help you can offer!

---

### Post by Skripka on 2008-12-17
> **JimTDI said:**
> Maybe one of you more experienced Opera users can help answer a question for me.

I see there is now an update to 9.63 Opera.  I have 9.62 installed.  I know how to upgrade on Windoze - but in Ubuntu, how do I upgrade Opera?

If I download the .deb file for 9.63, will it upgrade my existing Opera install, or do I somehow need to remove the prior installed Opera (seems like quite a job, cause there's ALOT of files it installed), and then install the new .deb file ??

Thanks for any help you can offer!

Just download the new deb and install.  No need to go mucking about in Synaptic.

---

### Post by jerome1232 on 2008-12-17
Well yes you can download the .deb and install it, it will automatically upgrade opera.

I like to add Opera's repository so that opera simply gets updated the same way the rest of my system does (it gets checked once a day and if there's an update avaible you get a notification in your system tray)

If you wanted to add their repo here's Opera's instructions on how to do it [http://www.opera.com/support/kb/view/841/](http://www.opera.com/support/kb/view/841/)

---

### Post by JimTDI on 2008-12-17
> **jerome1232 said:**
> Well yes you can download the .deb and install it, it will automatically upgrade opera.

I like to add Opera's repository so that opera simply gets updated the same way the rest of my system does (it gets checked once a day and if there's an update avaible you get a notification in your system tray)

If you wanted to add their repo here's Opera's instructions on how to do it [http://www.opera.com/support/kb/view/841/](http://www.opera.com/support/kb/view/841/)

If I installed 9.62 from the .deb file, and now I add Opera's repositories, and use that to keep Opera up to date, will I risk screwing my system up?  Thanks for your help!

---

### Post by JimTDI on 2008-12-17
> **Skripka said:**
> Just download the new deb and install.  No need to go mucking about in Synaptic.

OK, great!  Thanks!!

---

### Post by jerome1232 on 2008-12-17
> **JimTDI said:**
> If I installed 9.62 from the .deb file, and now I add Opera's repositories, and use that to keep Opera up to date, will I risk screwing my system up?  Thanks for your help!

No you wouldn't mess your system up. If you wish to add their repos here's an easier way to do it:

System->Administration->Software Sources

Now click the "Third-Party Software" tab

click "add"
add the line below
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

now click close

Ignore any errors and add their gpg key to elimnate those errors

Open a terminal Applications->Accessories->Terminal

```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
exit
```

I know it seems difficult at first (all this extra work) but as you accumulate software it becomes easier to keep your software updated if it's all in a repository. Just my personal opinion.

---

