---
title: "Where does Firefox store proxy-connection settings?"
date: 2009-01-01
forum: General Help
---

### Post by pytheas22 on 2009-01-01
I use an ssh proxy with Firefox frequently.  It works great, but it's sort of tedious to have to open up Firefox preferences, click the 'Advanced' tab, open the configuration window for the network and tell it to switch to ssh proxy, and then open up a terminal and log into my ssh server before the changes can take effect.

Consequently, I'd like to write a script that would automatically switch between an ssh proxy and normal settings for my Firefox connection.  In order to do that, I need to know where exactly Firefox stores information about how it should connect, since that's the file that my script would need to operate on.

I could probably figure this out on my own with enough trial and error inside my ~/.mozilla folder, but if anyone could just tell me which file to edit, I'd be grateful.

---

### Post by The Cog on 2009-01-01
I seem to remember there is a firefox add-on that makes switching proxies nice and easy. I can't remember the name, but I'm sure there is one. It's worth a look.

---

### Post by TheMyself on 2009-01-01
It's called Foxyproxy. I've not used it.


[https://addons.mozilla.org/en-US/firefox/addon/2464](https://addons.mozilla.org/en-US/firefox/addon/2464)

---

### Post by nikgare on 2009-01-01
I prefer ProxySel addon

---

### Post by Ahadiel on 2009-01-01
You could also use tsocks.

---

### Post by pytheas22 on 2009-01-01
Thanks for the suggestions.  An extension would help.

I'm still interested in the script, however, because I could use it to create the ssh connection as well as switch FF proxies.  If I used an extension, I'd still have to open up a terminal and ssh into my server before it would work.

All the same, an extension would still make things considerably more convenient; thanks for the suggestions so far.

---

### Post by The Cog on 2009-01-02
Try looking in this file:
**~/.mozilla/firefox/*.default/prefs.js**
I have nine lines in there that mention the IP address of my proxy. No other file in there mantions it by IP address, so I guess that's the file to go for. I don't know if you have to restart firefox - probably.

---

### Post by pytheas22 on 2009-01-04
> Try looking in this file:
~/.mozilla/firefox/*.default/prefs.js
I have nine lines in there that mention the IP address of my proxy. No other file in there mantions it by IP address, so I guess that's the file to go for. I don't know if you have to restart firefox - probably. 

Thanks; I figured it out using this information.  When connection via an ssh proxy is enabled, prefs.js contains this line:
```

user_pref("network.proxy.type", 1);
```

Using default settings, that line doesn't exist at all.

Now I can just write a script to add or remove that line while simultaneously opening an ssh tunnel to my server, and in principle it will all work.

---

### Post by Matthuffy on 2009-03-14
about:config and type proxy ;)

and to update them, say using JavaScript you can do this:

```
function setProxy(){
netscape.security.PrivilegeManager
      .enablePrivilege("UniversalBrowserAccess UniversalXPConnect");
      var prefs = Components.classes["@mozilla.org/preferences-service;1"]
                  .getService(Components.interfaces.nsIPrefBranch);
 
         prefs.setIntPref("network.proxy.type", 1);

	 prefs.setCharPref("network.proxy.ftp", "12.12.12.12");
	 prefs.setIntPref("network.proxy.ftp_port", "8080");

	 prefs.setCharPref("network.proxy.gopher", "12.12.12.12");
	 prefs.setIntPref("network.proxy.gopher_port", "8080");

	 prefs.setCharPref("network.proxy.http", "12.12.12.12");
	 prefs.setIntPref("network.proxy.http_port", "8080");

	 prefs.setCharPref("network.proxy.socks", "12.12.12.12");
	 prefs.setIntPref("network.proxy.socks_port", "8080");

	 prefs.setCharPref("network.proxy.ssl", "12.12.12.12");
	 prefs.setIntPref("network.proxy.ssl_port", "8080");

      }
```
you can call that either when you visit a certain page/place. and if you call the same but will all fields blank then it will turn the proxy off also.

---

### Post by pytheas22 on 2009-03-14
Matthuffy: that's a very nice script, thanks!  Unfortunately I don't know javascript myself, or I might have thought to go that route instead of bash.

---

