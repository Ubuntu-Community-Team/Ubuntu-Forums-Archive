---
title: "hate restoring panel in ubuntu back 2 their default settings"
date: 2011-05-05
forum: Desktop Environments
---

### Post by trpted on 2011-05-05
Every time after I boot up, I have to follow the info at

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Do you have any ideas on to make sure that I do not have to do that almost every time I boot up?

I am using the 10.04 LTS release

Thanks.

---

### Post by Jesus_Valdez on 2011-05-05
Why do you have to do that? What's the problem with the panel?

---

### Post by Megaptera on 2011-05-05
> **trpted said:**
> Every time after I boot up, I have to follow the info at

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Do you have any ideas on to make sure that I do not have to do that almost every time I boot up?

I am using the 10.04 LTS release

Thanks.

While you try to get a permanent fix you could in the meantime try this 

"PanelRestore, that allows you to quickly and easily restore the default Gnome panels in Ubuntu and to backup and restore your existing custom panel configurations." 
[http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/](http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/)

---

### Post by wilee-nilee on 2011-05-05
> **trpted said:**
> Every time after I boot up, I have to follow the info at

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Do you have any ideas on to make sure that I do not have to do that almost every time I boot up?

I am using the 10.04 LTS release

Thanks.

How about a screen shot of the before and after of the panel. Use the paperclip in the reply panel to upload and post the pics.

---

### Post by bwallum on 2011-05-05
> **trpted said:**
> Every time after I boot up, I have to follow the info at

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Do you have any ideas on to make sure that I do not have to do that almost every time I boot up?

I am using the 10.04 LTS release



I'm not sure if you have a misbehaving panel or if you wish simply to return to the default setting.

To reset the panels try ```
killall gnome-panel
```. You should see the panels disappear and then regenerate. Does that do it for you or would you like to change the panels to get back to default?

---

### Post by trpted on 2011-05-06
> **Megaptera said:**
> 
"PanelRestore, that allows you to quickly and easily restore the default Gnome panels in Ubuntu and to backup and restore your existing custom panel configurations." 
[http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/](http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/)

That is cool.

Is there a way to make that Restore Panel Settings automatic?

Thanks.

---

### Post by trpted on 2011-05-06
Update..

It used to be everytime after I bootup. Now, it seems less often. We need to find out, how often.

In the meantime, I guess the answer is every between two days / week.

---

### Post by trpted on 2011-05-06
> **bwallum said:**
> I'm not sure if you have a misbehaving panel or if you wish simply to return to the default setting.


Ok, upon refection..

I have a misbehaving panel (or misbehaving panels).

> **bwallum said:**
> To reset the panels try
```

killall gnome-panel

```
You should see the panels disappear and then regenerate. 

Does that do it for you?


Thank you for the interesting tip.

Unknown at this time, but I will try that soon..

---

### Post by Megaptera on 2011-05-06
> **trpted said:**
> That is cool.

Is there a way to make that Restore Panel Settings automatic?

Thanks.

Sorry, I don't know as I've not tried.

---

### Post by trpted on 2011-05-08
> **wilee-nilee said:**
> How about a screen shot of the before and after of the panel. Use the paperclip in the reply panel to upload and post the pics.

Since you asked for it and it happened again, here you are...

---

### Post by trpted on 2011-05-10
> **bwallum said:**
> 
To reset the panels try ```
killall gnome-panel
```. You should see the panels disappear and then regenerate.

It happened again. Grr.

I tried your tip and it worked. :)

--

Do you (or any one) else have any ideas on how to fix this permanently?

Thanks

---

### Post by bwallum on 2011-05-10
I found that it fixed it after a couple of times. When you get the panel as you like it then restart the system and the panel should come back up as you left it.

---

### Post by trpted on 2011-05-10
> **bwallum said:**
> I found that it fixed it after a couple of times. When you get the panel as you like it then restart the system and the panel should come back up as you left it.

Ok.

I will try that, if I have not already - soon...

If that does not work, what would that mean / what do you suggest?

Thanks

---

### Post by bwallum on 2011-05-10
I never needed to do anything else. I guess if it didn't settle down I would look to writing to a conf file but I don't think you will need to do that. Generally its a good idea to keep everything as 'standard' as possible rather than have a lot of tweaks that you may lose track of.

---

