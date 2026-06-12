---
title: "Wired texture on EMERALD window borders"
date: 2010-01-06
forum: Desktop Environments
---

### Post by felipao on 2010-01-06
Hello All,

Thanks for looking, I am very new to Ubuntu and Unix in general but so far I am loving it all and I have ditched every other OS from my home!

I have a small annoyance that I have been trying to fix for a while without success. I have emerald managing my windows with the same theme (simple & nice) on both my laptop and my desktop. Both configurations are exactly the same, but on my laptop I get a wired texture thing (black and white) that i cannot get rid of. I would like to have my window borders plain black with a little opacity. I would like any suggestions on how to get rid of the texture.

I have attached a screenshot so you can see what I am talking about.

This should be something very simple to fix, but I cant seem to find a solution anywhere around this forum or on google.

Thanks in advance,
Felipe


[IMG]http://lh5.ggpht.com/_lFJA_rnehCM/S0VJ3OzLrXI/AAAAAAAABXo/fTCUbHfR0PE/s640/Screenshot.png[/IMG]

---

### Post by jonest1 on 2010-01-06
I downloaded the theme and took a look (looks great!).  The only thing I can think of is that the engine may have been changed.

1.  Open the Emerald Theme Manager.
2.  Select the theme.
3.  Click the 'Edit Themes' tab.
4.  In the 'Frame Engine' tab, do you see the engine as vrunner?  If not, then select it and see if it works. 
5.  Once the result is good, go to the Theme tab and save the theme.

It almost looks like you may be using the Pixmap engine with a graphic for the top titlebar.

If this doesn't work, you may want to remove the theme using the Emerald Theme Manager and add it back in.  Also, you may want to check the file to ensure it is okay.  Run 'md5sum filename' on both of your systems and the checksum should be identical.  If not, copy the file from your desktop to your laptop and add it back in.

---

### Post by felipao on 2010-01-06
> **jonest1 said:**
> I downloaded the theme and took a look (looks great!).  The only thing I can think of is that the engine may have been changed.

1.  Open the Emerald Theme Manager.
2.  Select the theme.
3.  Click the 'Edit Themes' tab.
4.  In the 'Frame Engine' tab, do you see the engine as vrunner?  If not, then select it and see if it works. 
5.  Once the result is good, go to the Theme tab and save the theme.

It almost looks like you may be using the Pixmap engine with a graphic for the top titlebar.

If this doesn't work, you may want to remove the theme using the Emerald Theme Manager and add it back in.  Also, you may want to check the file to ensure it is okay.  Run 'md5sum filename' on both of your systems and the checksum should be identical.  If not, copy the file from your desktop to your laptop and add it back in.

Hello jonest1,

Thank you for your time and help. 

I have tried your suggestions but the texture is still there. 
One thing that I noticed is that the texture is present in all my emerald themes, in every engine (except for Line). This texture also appears oh the shadows (which i normally disable, but I saw it when testing different configurations).

It makes me think that this is not something related to the specific theme but some kind of emerald configuration or something else.... any ideas??

Thanks again! :-)

---

### Post by felipao on 2010-01-06
Ok, I was able to remove the texture..... somehow.

I was playing with the GTK theme settings and after that the texture disappeared. I am not sure what made it go away but i am suspecting that changing the boarder theme under GTK influenced it somehow. I am sorry I don't have the knowledge to explain it any deeper but I am sure happy to have found a solution.

Thanks again!!!

---

