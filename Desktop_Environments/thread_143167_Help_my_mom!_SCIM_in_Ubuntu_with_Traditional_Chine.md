---
title: "Help my mom! SCIM in Ubuntu with Traditional Chinese language"
date: 2006-03-11
forum: Desktop Environments
---

### Post by newdave on 2006-03-11
Hi,

I don't know if there is a really obvious solution to this that I just skipped over, but I'm very new to linux and I can't figure it out.

I'm setting up my mom's old AMD-K6 system to run with Ubuntu. I set it up using Traditional Chinese (TW) as the default language. Everything installed fine and it works. I was planning on using SCIM for chinese input method but it doesn't seem to work when the default language is Chinese. SCIM works fine when everything is English. 

I checked the Language Selector and writing aids is checked, but no Chinese input method seemed available. I thought there might be some conflict so i unchecked it. 

In Chinese, I opened up a terminal and started up SCIM (sudo scim -d) and the console comes up but i can't change it to anything but "English/Keyboard".

Is there an input method already there in the Chinese Writing Aids and I'm too stupid to realize? If not, does anyone know how i can get SCIM to work?

I'm using a US keyboard.

Please help me help my mom!

Dave

---

### Post by tsb on 2006-05-09
same problem here  :(

anyone?

---

### Post by tsb on 2006-05-09
got it figured out

add a new file called ".xsession" in the home directory

paste: 

export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
gnome-session

in the file and save it

Go to "System" -> "Perferences", and select "Sessions". In "Startup Programs", add the command "scim -d".

After a reboot/new login everything should be golden

;)

---

