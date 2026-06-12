---
title: "Move &amp; delete folders for Squeezecenter plugins"
date: 2009-01-27
forum: General Help
---

### Post by jmacknmo on 2009-01-27
I have installed several plugins for Squeezecenter & they mostly seem to work well. In reading further, I see that I have installed them in the wrong directory. I have been trying to fix the situation, but need some help. I have been able to copy the directory ... 

sudo cp -R /usr/share/perl5/Slim/Plugin/  /usr/share/squeezecenter/Plugins/

but this copied everything to /usr/share/squeezecenter/Plugins/Plugins.
What did I do wrong? 

How do I move them to .../squeezecenter/Plugins/ & remove the .../Plugins/Plugins directory?

I then also have to go back & remove the some directories from /usr/share/perl5/Slim/Plugin/. I just realized that some of the directories were probably already there before I started the plugin experimentation so I will have to pick & choose the directories to delete. 

Can I delete by date created? I don't see a way to show the create date in Nautilus. Is there a way to delete the directories in Nautilus? I always get "Permission denied" even in /usr/share/squeezecenter/Plugins/Plugin.

Thanks for you help!!!

---

