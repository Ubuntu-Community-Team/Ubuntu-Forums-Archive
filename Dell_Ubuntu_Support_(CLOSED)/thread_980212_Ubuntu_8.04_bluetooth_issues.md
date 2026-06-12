---
title: "Ubuntu 8.04 bluetooth issues"
date: 2008-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JohnCL530 on 2008-11-12
I have a Dell Mini 9 running Ubuntu 8.04 and I have a problem getting the mouse paired after I inadvertently made a mistake.

I accidentally deleted the mouse device from the "Bonded devices" window, and now when I try to connect the mouse again I get "Cannot pair with the device: Input already exists"  I have done all that I can to try to figure this out but have had no luck at all.  I am new to Ubuntu, so any help would be appreciated.

---

### Post by sultanoswing on 2008-11-13
Yeah - I found the BT Mouse to be a bit hit and miss in 8.04 too. Sometimes it would detect and start at bootup, othertimes not. Some searching ought to provide a few fixes, and you can also try what worked for me (in a console / terminal):

```

sudo /etc/init.d/bluetooth restart

```

You'll need to ensure your mouse is at least recognised and paired. Again, there a number of threads on this.

I can't comment on whether this is fixed in 8.10 (on my XPS 1330) since I've misplaced my BT Mouse!

---

### Post by bozackt on 2008-11-21
I just get a Mini 9 with a Dell bluetooth travel mouse. The mouse worked exactly once. Now I have the same problem as you have.

Did you find a solution.

---

### Post by Boss Happy on 2009-02-12
Exact same issue.  My Dell Bluetooth mouse worked yesterday (when I received the Mini 9).  Today it's not connecting.  Also, in an attempt to recreate the pairing, I also deleted the device from the "Bond" list, and now I get the "Already paired." message.

---

### Post by bozackt on 2009-02-12
I had the same problem when I first got my Mini 9. One way that worked for me to get Ubuntu to recognize the Bluetooth mouse again was to put the mouse in pairing mode and run the following command:

sudo hidd --search

This always worked.

The large Dell Ubuntu 8.04 update that was released a few weeks age seems to have solved the problem -- at least for me.

---

### Post by Boss Happy on 2009-02-15
I've upgraded to Ubuntu 8.10 and the bluetooth problem persists.  The only advantage is you can delete the connection then re-add it and it will work again.

Also, I've confirmed Bozackt's solution (using "sudo hidd --search", with 8.10 you have to install a deprecated package) and it works.

Thanks Bozackt

---

### Post by bigbrovar on 2009-02-15
have you tried blueman ? its better than the default bluetooth manager that comes default with gnome. [http://bigbrovar.wordpress.com/2009/02/14/blueman-an-awesome-bluetooth-manager-for-ubuntu/ ]("http://bigbrovar.wordpress.com/2009/02/14/blueman-an-awesome-bluetooth-manager-for-ubuntu/")

---

### Post by debrowning on 2009-02-15
I see that I am not alone.  Got a Mini 12 with Ubuntu this week and the BT Mouse worked exactly once as well.  Will try the suggestions

---

### Post by joe.man on 2009-02-28
> **bozackt said:**
> 
sudo hidd --search


I just got a mini 12 and the mouse worked 1 time. After rebooting, the mouse never worked again. I spent 2 days looking for the solution and Bozackts' solution worked perfect for me.

---

### Post by punkboat on 2009-09-26
[quote=bozackt;6725778]
sudo hidd --search

Thank you from another satisfied customer. Worked.

---

