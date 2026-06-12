---
title: "Wine"
date: 2006-04-24
forum: Desktop Environments
---

### Post by morequarky on 2006-04-24
Hi.  i followed the directions listed on this board on wine installation, except i installed the wrong browser language.  anyways, for a few moments internet explorer worked.  i updated wine like the howto said and internet explorer didn't work anymore.  i had some error writing to some dll or some such thing, probably because i installed the wrong language.  anyway, i would like to do the installation over again and would like to know how to delete/uninstall wine completely and start the howto over.  this time i may not update wine.  I only need ie for a few websites, outside of that, my wife and i only use ubuntu.

honestly the issue with the websites is activex support.  The websites use a lot of activex to make sure your computer is secure.  banking websites. if there is an activex program somewhere that will allow us to login and surf the banking websites in firefox, i would be extremely interested.  i am not sure wine with ie has the activex support required; yesterday when i had ie working for a short time, it seemed to work, but very slow.

i think reinstalling wine and starting over would be best.

thanks again, you've been great. ubuntu is fantastic.

quarky

---

### Post by foolsh on 2006-04-24
**sudo apt-get remove wine** 
will remove wine

---

### Post by morequarky on 2006-04-24
FOOLSH:

Will that remove all the windows installations aswell?

Thanks.

edit:  How do I remove winetools or is it best to keep it because i am going to reinstall anyways?

---

### Post by pelle.k on 2006-05-28
"rm -R .wine" in your home directory will remove the hidden wine directory, thus removing wine configuration and installed windows programs.
as good as new.

---

### Post by dtlinker on 2006-06-05
I had played with wine a little under breezy, and now am trying the same with dapper. I have a fresh install of dapper.

I am unable to get any significant programs to work. I installed the latest wine, used winetools to try to set up the base and get internet explorer installed, but that installation hangs near the end, and the resulting installation will not run. 

I also tried some other program installers that I was able to get to work before, but now they just start up and hang (Atmel's AVR Studio, for example).

Is the current wine broken, or is it broken on Dapper, or am I doing something wrong?

---

### Post by pelle.k on 2006-06-06
Wine on dapper is much better than on breezy. Winetools is deprecated and NOT recomended. winecfg, uninstall, and so on is recommended instead.
Try using a ntive .dll if it complains about not finding something particular in debug message...

---

