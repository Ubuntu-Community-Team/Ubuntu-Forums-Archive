---
title: "Flash installation failed"
date: 2006-10-12
forum: Desktop Environments
---

### Post by dgermann on 2006-10-12
Hi--

Have been trying to get Flash installed on my 6.06 box.

After trying with Synaptic and even the Macromedia site, I have been following the instructions on [DapperGuide]("http://doc.gwos.org/index.php/DapperGuide#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox").

The install of the flashplugin-nonfree goes without any reported problem. Then this:

```
doug@doug2:/etc/apt$ sudo update-flashplugin
automatic installation failed due to network problems or upstream changes
```

Thinking it was a repositories problem, I replaced my /etc/sources.list as suggested, but to no avail. Still get that same error message.

On this [bug site]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/62060") one person solved it this way: 
> I can confirm the problem and I solved it by simply adding some FAIL="false" into /usr/sbin/update-flashplugin.

Now I looked at that file and have no idea where to start.

Perhaps I already have Flash installed--but I don't know how to tell.

So, is there hope, or just give up?

---

### Post by aysiu on 2006-10-12
I have Flash installed, and I've never run the command *sudo update-flashplugin*.

Here are some other methods, outlined in more detail than the Dapper Guide:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by s_p_a_r_k_y on 2006-10-12
to see if it is working within firefox, go to about:plugins in the address bar, and it will either display shockwave flash, or not in ur list of plugins.

---

### Post by dgermann on 2006-10-13
aysiu--

Thanks, aysiu! I went to that site and then did the command line install. I was able to get that RISD site that he refers to, so it **looks** like that is working. But...

s_p_a_r_k_y--

...But I'm not sure. I do not see anything on my Firefox that says "About Plugins." Not sure which part of it is the "address bar."

Thanks, s_p_a_r_k_y!

And the question that started this for me--I am not able to view videos on video.yahoo.com, but can from video.google.com. I had supposed that this was because of a missing Flash. Any ideas what I should be doing?

Thanks, folks!

---

### Post by aysiu on 2006-10-13
The videos on Google Video are definitely Flash.

I don't know what Yahoo!'s videos are...

**Edit**: Maybe you need Flash 9 for Yahoo!?
If so, [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) may help.

---

### Post by dgermann on 2006-10-16
aysiu--

Thanks much!

I tried the "trick" method and it did not work. Somehow, the program overwrites this file and reverses my spoof.

Have tried to install wine before, so it is not something I relish. I guess I will wait till 2007 for the native linux flash.

BTW, video.yahoo has an advanced search which allows you to choose different types of video files. Some I could open, and some not, but that was a couple days ago, so I don't remember which ones worked.

Thanks for your help.

Oh, had another identical Ubuntu 6.06 box without flash. Went to a site with flash, got the you need a plugin screen, clicked on it, and it was installed in about 2 seconds. Slick.

Thanks, aysiu!

---

