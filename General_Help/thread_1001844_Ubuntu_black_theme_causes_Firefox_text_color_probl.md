---
title: "Ubuntu black theme causes Firefox text color problems"
date: 2008-12-04
forum: General Help
---

### Post by trendal.toews on 2008-12-04
I'm using the black theme in hardy but in Firefox some of the text input columns are the same color as the text which makes them hard to use.  If you highlight the text you can see it.  Is there a way to apply this theme just to Ubuntu and not to Firefox?

---

### Post by IceReaver75 on 2008-12-04
> **KatmanHH said:**
> I'm using the black theme in hardy but in Firefox some of the text input columns are the same color as the text which makes them hard to use.  If you highlight the text you can see it.  Is there a way to apply this theme just to Ubuntu and not to Firefox?


you can try to use this command in a terminal:
cp /usr/share/themes/SlicknesS/userChrome.css $HOME/.mozilla/firefox/*.default/chrome

it is used with some dark themes to fix that.

Edit: you want to changes the name after /themes to the theme name you are using so like this actually

cp /usr/share/themes/your theme name/userChrome.css $HOME/.mozilla/firefox/*.default/chrome

---

### Post by binbash on 2008-12-04
Above post should do the trick, you can also solve your problem by installing Nasa theme to your firefox

---

### Post by NastyT23 on 2009-01-21
Nope didn't work for me...i get an error...
> terry@terry-desktop:~$ cp /usr/share/themes/Descent/userChrome.css $HOME/.mozilla/firefox/*.default/chrome
cp: cannot stat `/usr/share/themes/Descent/userChrome.css': No such file or directory
terry@terry-desktop:~$ 

I have the Nasa them installed as well but it still doesn't help with being able to see the text in some web pages and input boxes....this is getting annoying. And im using ubuntu-ultimate edition, it already had some extra fonts installed so i dont know what the default ones were. I've seen some other posts suggestion to remove the extra fonts but i dont know which are the default anymore.
HELP! Thanks!

---

