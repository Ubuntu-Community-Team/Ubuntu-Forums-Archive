---
title: "cut and paste under dapper"
date: 2006-04-15
forum: Desktop Environments
---

### Post by uahrur on 2006-04-15
hi, 

I am looking for a way to restore the old way 
of cuting and pasting text under dapper (select with the left mouse button then paste/release with the middle button). Some one has a clue ?

thanks.

---

### Post by Qrk on 2006-04-15
As far as I know, nothing has been changed.

The middle button paste feature is in part of X, I believe. It doesn't use the normal paste through Gnome's clipboard. If you highlight text with your mouse and then middle click somewhere else, it should paste that text. 

If you right click text and select copy, you need to right click to select copy to paste that text. You can even have your middle mouse button paste different text than your right mouse button.

---

### Post by uahrur on 2006-04-16
thanks for the answer

 |As far as I know, nothing has been changed.

     but it has changed under dapper

 |The middle button paste feature is in part of X, I believe. It doesn't use the normal paste through        |Gnome's clipboard. If you highlight text with your mouse and then middle click somewhere |else, it |should paste that text.

      it does't work any more for me

|If you right click text and select copy, you need to right click to select copy to paste that text. You |can even have your middle mouse button paste different text than your right mouse button.

   This the way i have to use now and it is very very boring.

Thanks again for answering me.

---

### Post by Ramses de Norre on 2006-04-16
Do you have the Emulate3Buttons option set to true in xorg.conf for your mouse? If so try disableing it. (and restart X to apply the new setting)

---

### Post by matt-e on 2006-05-08
I just noticed this same problem today.  I have a Logitech USB wireless laptop mouse and under Dapper recently (possibly after upgrading in the past few days) I suddenly couldn't paste with the middle mouse button (I realize some people hate this but I've been using it as a programmer for years and am addicted to it).

I tried switching Emulate3Buttons to false but that didn't change things.  I noticed that in my old xorg.conf the Mouse Protocol was set to "ImPS/2", but in my current xorg.conf it was "ExplorerPS/2".  I modified xorg.conf to change that back to ImPS/2 and now it works fine.

It's possible you're having this same problem :-k

---

