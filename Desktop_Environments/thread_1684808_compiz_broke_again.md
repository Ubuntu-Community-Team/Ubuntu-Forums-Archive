---
title: "compiz broke again"
date: 2011-02-09
forum: Desktop Environments
---

### Post by sevenenemy on 2011-02-09
not sure if its an update that broke it would like peoples feedback on that to see if thats it... i was changing things around in compiz but from past experience i dont think anything i changed could cause this crash. the fusion icon wont load and nothing compiz related will load. im trying to remember the name of the package i downloaded to make a bunch of themes work right, 'ubuntulooks' was missing and i tried to install that and it threw me a bone and told me what to apt-get, but now i remember thats what broke compiz. i am trying right now to see if i can fix it by changing to a different theme....but i cant seem to do that. if i remember right i installed or tried to install 'gtk2-engines-ubuntulooks' and it told me it was obsoleted and 'human-themes' replaced it, which i now have installed and my question now is does anyone know if 'human-themes' package conflicts with compiz or have any knowledge of other possible conflicts i may have overlooked relating to this topic also please bare in mind that i am running ultimate edition 2.8 tweaked all to hell with ubuntu studio and medibuntu and other various repos but its never crashed til now and its just compiz

---

### Post by JOHNNYG713 on 2011-02-09
You might want to ask about this **at** [http://ultimateedition.info/](http://ultimateedition.info/) **and **[http://www.ultimateeditionoz.com/](http://www.ultimateeditionoz.com/) Since you are running **Ultimate Edition** ! :guitar:

---

### Post by sevenenemy on 2011-02-09
not sure if its an update that broke it would like peoples feedback on  that to see if thats it... i was changing things around in compiz but  from past experience i dont think anything i changed could cause this  crash. the fusion icon wont load and nothing compiz related will load.  im trying to remember the name of the package i downloaded to make a  bunch of themes work right, 'ubuntulooks' was missing and i tried to  install that and it threw me a bone and told me what to apt-get, but now  i remember thats what broke compiz. i am trying right now to see if i  can fix it by changing to a different theme....but i cant seem to do  that. if i remember right i installed or tried to install  'gtk2-engines-ubuntulooks' and it told me it was obsoleted and  'human-themes' replaced it, which i now have installed and my question  now is does anyone know if 'human-themes' package conflicts with compiz  or have any knowledge of other possible conflicts i may have overlooked  relating to this topic also please bare in mind that i am running  ultimate edition 2.8 tweaked all to hell with ubuntu studio and  medibuntu and other various repos but its never crashed til now and its  just compiz

---

### Post by overdrank on 2011-02-09
Hi and please do not create multiple threads on the same issue. Threads merged :)

---

### Post by sevenenemy on 2011-02-10
sorry it didnt show up in my threads list for a few minutes and i thought it got deleted due to swearing in the thread. the ultimate edition forum is kinda stale with very little feedback and ultimate edition is just maverick with extra repos, its not a different os.

---

### Post by sevenenemy on 2011-02-10
so i put this on the ue forums already but its gonna take awhile for it to be handled anybody got any ideas

---

### Post by sevenenemy on 2011-02-25
i am getting this error from ubuntu tweak which seems to be the only one i can find at all from compiz because i cant even get anything related to compiz to open or be interactive in any way 

Distribution: Ubuntu 10.10 maverick
Application: Ubuntu Tweak 0.5.10
Desktop: gnome

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py", line 502, in setup_notebook
    page = module()
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/compiz.py", line 325, in __init__
    self.create_interface()
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/compiz.py", line 343, in create_interface
    hbox.pack_start(self.create_edge_setting(), True, False, 0)
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/compiz.py", line 475, in create_edge_setting
    self.TopLeft = self.create_edge_combo_box("TopLeft")
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/compiz.py", line 447, in create_edge_combo_box
    if CompizPlugin.is_available(k, v):
  File "/usr/lib/python2.6/dist-packages/ubuntutweak/modules/compiz.py", line 127, in is_available
    getattr(cls.context.Plugins[name], target).has_key(setting)
  File "compizconfig.pyx", line 945, in compizconfig.Plugin.Display.__get__
  File "compizconfig.pyx", line 766, in compizconfig.Plugin.Update
KeyError: 'active_plugins'

thinking it was a human-theme compatibility error i removed that and no luck i know a little as3 and can see that the error involves creating the edges for combo boxes and that it conflicts with active-plugins or something along those lines but where to go from here is beyond me

any ideas would be greatly appreciated

thanks

---

### Post by sevenenemy on 2011-02-25
ok so another quick update

i removed all the compiz related packages and then reinstalled human-themes. then i re installed all the compiz packages. now i can access and set options for compiz and the fusion icon loads again and things look hopeful, but it looks like this version of compiz is different from my last as it has no sphere or cylinder views and my add helper is gone from the accessibility options.

any ideas?

things are lookin up in NH

---

### Post by sevenenemy on 2011-02-25
and the package from the first post is human-theme not themes

---

