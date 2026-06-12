---
title: "Server setup help."
date: 2009-02-02
forum: General Help
---

### Post by linuxisevolution on 2009-02-02
I have one server already setup, that serves all the sites in my sig. I have another server now setup ( actually an old mac ) that holds some HTML object files. I would like the first server to refer to the second to get the files in the html page, but the second server is not hooked up to the WAN, just the LAN. 

ROUTER: 24.3.84.251
Main server: 192.168.1.125
Other Server: 192.168.1.34

**1. How would I make the server at 192.168.1.125 refer to 192.168.1.34?** If you type the router's ip in your browser, you will get to a simple site on the Main Server. 
**2. Would the code for this be in the main html page, or would it be somewhere in the apache configuration?**

Thanks for any help!


**Example: 24.3.84.251 ->> DMZ ->> 192.168.1.125. But, can I go like this?: 24.3.84.251 ->> DMZ ->> 192.168.1.125 ->> 192.168.1.34**

---

### Post by CrusaderAD on 2009-02-02
I hope I'm understanding this correctly... but here's a shot at it. In your apache configuration, under "sites available" you should find your config file for that particular site. Can you mount the shared drive (with the html docs) and then adjust the location in the config file so that the server looks in this share? This way the enabled site is pulling from the directory set in the config file. I hope I explained my theory well enough!

---

### Post by linuxisevolution on 2009-02-02
> **raptormanad said:**
> I hope I'm understanding this correctly... but here's a shot at it. In your apache configuration, under "sites available" you should find your config file for that particular site. Can you mount the shared drive (with the html docs) and then adjust the location in the config file so that the server looks in this share? This way the enabled site is pulling from the directory set in the config file. I hope I explained my theory well enough!

This sounds easy, and should work. I am very great full for your post, I didn't think anyone would understand :D . How do I do this? Simply mount the mac as NFS or whatever ( what does a mac use to share files, anyway? ) and then I could simply direct the server's web pages to to the MAC! AWESOME! I'll let you know when I get this to work -I have to figure out how to get Debian to mount my mac's share...

---

### Post by linuxisevolution on 2009-02-02
I got it to work! Here is an example page on the mac:

[http://24.3.84.251/apache2-default/mac/mac/Default.html](http://24.3.84.251/apache2-default/mac/mac/Default.html)

---

### Post by CrusaderAD on 2009-02-03
Glad to see you got it working!

---

