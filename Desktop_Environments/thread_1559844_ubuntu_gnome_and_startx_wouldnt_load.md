---
title: "ubuntu gnome and startx wouldnt load"
date: 2010-08-24
forum: Desktop Environments
---

### Post by Explor on 2010-08-24
I am a newbie to Ubuntu and I am having problem with loading Gnome and startx. I have ubuntu 9.1 installed on my Dell Inspiron E1505 system. The problem started when gnome-power-manager started giving error regarding configuration settings not installed properly. I tried to google it and after lot of searching I figured out that my root directory is almost full. Moving some folders helped me solve the problem. But in the meantime I think I have screwed up some where. Now my Gnome or startx wouldnt load. Ubuntu logins my user profile and after that just sits that with the cursor revolving. When I press ctrl+Alt+F1 it gives no errors. Then I stop gdm by
"sudo service gdm stop"
and start startx by
"startx"
seems like Startx also doesnt start. checking again by Ctrl+Alt+F1 shows that its still running giving message like

setting master
stopping master..

Can you please help me solve the problem?

Thanks

---

### Post by Explor on 2010-08-24
I have attached the files xsession_errors and Xorg.0.log.

Also while rebooting in the recover mode the systems keeps running and doesnt give a prompt. Only while rebooting in normal mode and pressing Ctrl+Alt+F1 am I am able to get command line.

---

### Post by Shasha.Ehome on 2010-08-24
Excellent Idea! I've added it.

---

### Post by Explor on 2010-08-24
can you please be specific?

Thanks

---

