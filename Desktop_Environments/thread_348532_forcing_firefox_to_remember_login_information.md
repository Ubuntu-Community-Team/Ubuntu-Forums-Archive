---
title: "forcing firefox to remember login information?"
date: 2007-01-28
forum: Desktop Environments
---

### Post by 13east on 2007-01-28
is there anyway to force websites to remeber your login information? for my old windows machine, i got a hold of this javascript that would force any website to remember what you type in.  when i first installed badger i tried the same script on my desktop but it didn't work; and i don't remember the script anymore.  is there anyway to try this trick with edgy?

---

### Post by ewankho on 2007-01-28
You can set Firefox to remember your login information if you set it to remember your passwords. Tools->Options->Security, then check on remember password.

---

### Post by 13east on 2007-01-28
i know that already... i'm talking about the sites that won't allow you to save login information  for their sites.  i wanted to know if there is a way to force them to save it.

---

### Post by aysiu on 2007-01-29
Edit > Preferences > Privacy > Cookies > Accept cookies from sites should do it.

You should also make sure you have ownership of the Firefox preferences folder: ```
sudo chown -R 13east:13east /home/13east/.mozilla
```

---

### Post by 13east on 2007-01-29
already accepting cookies from sites...

---

### Post by ViaD on 2008-01-21
From [http://thatha.org/blog/force-firefox-to-remember-passwords/](http://thatha.org/blog/force-firefox-to-remember-passwords/)

```
javascript:(function(){var df=document.forms,dfe,i,j,x,y;df=document.forms;for(i=0;i<df.length;++i){x=df[i];dfe=x.elements;if(x.attributes['autocomplete']){x.attributes['autocomplete'].value='on';}for(j=0;j<dfe.length;++j){y=dfe[j];if(y.attributes['autocomplete']){y.attributes['autocomplete'].value='on';y.style.backgroundImage='url([http://ubuntuforums.org/images/smilies/icon_smile.gif)';y.style.backgroundRepeat='no-repeat';y.style.backgroundPosition='center](http://ubuntuforums.org/images/smilies/icon_smile.gif)';y.style.backgroundRepeat='no-repeat';y.style.backgroundPosition='center) left';y.style.paddingLeft='22px';}}}})();
```

Save the above link, navigate to your site, click the saved js link, enter username/password, verify
FF to remember...

---

