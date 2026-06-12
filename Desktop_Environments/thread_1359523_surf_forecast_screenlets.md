---
title: "surf forecast screenlets"
date: 2009-12-19
forum: Desktop Environments
---

### Post by venicequeen7706 on 2009-12-19
I'm new to linux and trying to use screenlets to put a surf forecast on my desktop and I can't find one. i have a few website with forecasts i like and they have a way to create widgets for a website. is there any way i can use that to set up a screenlet. these are two of the websites i would like to use if that helps any.

[http://www.swellinfo.com/surf-forecast/newport-rhode-island.html](http://www.swellinfo.com/surf-forecast/newport-rhode-island.html)

[http://www.surfline.com/surfdata/lola_surf_model.cfm?id=5112](http://www.surfline.com/surfdata/lola_surf_model.cfm?id=5112)

Any help would be greatly appreciated.

---

### Post by stinkeye on 2009-12-20
> **venicequeen7706 said:**
> I'm new to linux and trying to use screenlets to put a surf forecast on my desktop and I can't find one. i have a few website with forecasts i like and they have a way to create widgets for a website. is there any way i can use that to set up a screenlet. these are two of the websites i would like to use if that helps any.

[http://www.swellinfo.com/surf-forecast/newport-rhode-island.html](http://www.swellinfo.com/surf-forecast/newport-rhode-island.html)

[http://www.surfline.com/surfdata/lola_surf_model.cfm?id=5112](http://www.surfline.com/surfdata/lola_surf_model.cfm?id=5112)

Any help would be greatly appreciated.
You could use google gadgets to show a local surf forecast on your desktop.
Easiest way to install would be to first install [_[COLOR="DarkRed"]ubuntu-tweak[/COLOR]_]("https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9.2")
The i386.deb is your normal 32 bit install.Just choose the one for your distro .
Then in ubuntu-tweak > applications > third party sources
enable the google repository and refresh.
you can then install google-gadgets-gtk through synaptic.
Go to [_[COLOR="#8b0000"]http://globalsurfari.com/[/COLOR]_]("http://globalsurfari.com/")
and follow the instructions to register.
Run google-gadgets ... (menu > internet > google gadgets(gtk) )
Add a gadget by clicking on google icon in the panel and search for surfari.
Hover over the surfari gadget and click on menu > options and add the email address
that you used to log on to globalsurfari.com 
Now you should see a local surf forecast.

The window on the left is the google-gadget while the rounded windows on the right 
is what I use, and are drawn with conky and is a lot harder to setup
because you need to learn how to use conky with sed, grep and curl.
But if your interested this will get you started with conky.
[_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

### Post by venicequeen7706 on 2009-12-20
I'm trying that, but the options never finish loading for me. Not sure what to do. Also, I found that I can generate the code for a widget to be placed in a website using the surf forecasts I use already, is there any way to just put that code in something to make a widget on my desktop? 
thanks for the help

---

