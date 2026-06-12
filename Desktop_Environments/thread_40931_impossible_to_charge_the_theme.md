---
title: "impossible to charge the theme"
date: 2005-06-11
forum: Desktop Environments
---

### Post by souraka on 2005-06-11
hi  everyone
yesterday i tried to restart my ubuntu but i get a error message like :

"error chragind the theme human
bad size specifier scale"

then i get to a blue start page where it show me a place to put my username etccc( like the human theme ) but can't write on it   :|   it  is impossible to log (dont take the user name etc)

so now no way for me to access to ubuntu i am block on this page 

what i can do to resolve it

thanks a lot

---

### Post by Alexander Kirillov on 2005-06-11
[QUOTE=souraka]hi  everyone
yesterday i tried to restart my ubuntu but i get a error message like :

"error chragind the theme human
bad size specifier scale"

then i get to a blue start page where it show me a place to put my username etccc( like the human theme ) but can't write on it   :|   it  is impossible to log (dont take the user name etc)

so now no way for me to access to ubuntu i am block on this page 

what i can do to resolve it

thanks a lot[/QUOTE]
 1. after it starts, press ctrl-alt-F1. It wll give you a text terminal. Login there.
2. Make backup copy of gdm config file: 
sudo cp /etc/X11/gdm/gdm.conf /etc/X11/gdm/gdm.conf.backup

3. type sudo nano /etc/X11/gdm/gdm.conf
 This will open gdm configuration file in a simple text editor (nano) 
3. Find line GraphicalTheme=human and replace it with
GraphicalTheme=circles
Save the file and exit. 

Gdm will now use a different theme. 

4. Reboot (by running sudo shutdown -r now)

If everything is succesful, you will be now able to login in graphical mode.

---

### Post by souraka on 2005-06-12
thanks a lot !!!!!!!!

still learning how to be good with ubuntu and linux but you guys help me so much !!

thanks again

---

