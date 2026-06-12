---
title: "Default Disable Desktop Effects"
date: 2009-11-13
forum: Desktop Environments
---

### Post by steviefordi on 2009-11-13
I have setup an LTSP server running Jaunty. Everything works fine except new users on the system have desktop effects enabled by default.

This crashes most of the thin clients and the only way I can fix it is to log directly onto the server as the new user and turn it off through **System >> Preferences >> Appearance >> Visual Effects**. Their setting is then saved and everything is OK. As I have to do this for every user that hasn't logged on before this is quite tedious.

I would really like it if it was just disabled by default for new users. There must be a config file somewhere that is holding this setting? Any suggestions welcome...

---

### Post by steviefordi on 2009-11-16
Ok, I uninstalled everything compiz which forces the WM to be Metacity and fixes my problem.

This seems like a very heavy handed solution to a problem which can be solved with the GUI by clicking 'none' on the visual effects tab.

Surely that information is in a configuration file somewhere? It is remebered by Gnome when you log in so where is it recalling this information from?

I've looked through the Gnome registry with gconf-editor and can find nothing that matches the three options on the visual effects tab.

---

### Post by harmscon on 2009-11-23
G'day. Have you had any luck solving this? I have a network of 6 computers that have different hardware and would also like to set the default visual effect to none. Some of these computers are remotely accessed like your case so it would be a really sensible default for any network rollout.

I've just had an idea that from ccsm preferences it might be possible to use flat file instead of gconf, then save the settings from a default install, then set visual effects to none, save the settings again, and then compare the before and after. Then hopefully it will be easier to set a mandatory setting in gconf. I suspect that one little checkbox in Visual Effects has an impact on many gconf values.

I'm finished for today so I'll have to follow this up tomorrow.

---

### Post by steviefordi on 2009-12-02
I never did solve this 'properly', uninstalling compiz so Gnome defaults to metacity was the best I could do. This also prevents any users turning on desktop effects - which is good.

I think you're right about 1 checkbox setting several key-value pairs, I just couldn't work out which ones. If you do get to the bottom of it then let me know, I'd be very interested.

cheers
Steve.

---

### Post by joebrady on 2010-03-03
Anyone with any new bit of info for this problem?  I have run into the same, it's the one thing between me and a perfect XBMC/Full Ubuntu Desktop HTPC setup...

---

### Post by Cheile on 2010-05-12
<Typical Response> I can safely say that with my CONSIDERABLE sysadmin experience managing the 3 computers in my apartment and my friend's Xbox that there is NO reason that anyone would ever need to use the commandline.  Point-n-click-n-click-n-click-n-click is SO superior.  Just log in to all the systems and begin clicking... </Typical Response>   ;-) 


The following works on 9.10 (Karmic).  I'm not sure about 10.04 (Lucid), but it should work. 

Create a file called /etc/X11/Xsession.d/98x11-custom_force-metacity with a single line that reads: 
/usr/bin/gconftool-2 --type string --set /desktop/gnome/session/required_components/windowmanager metacity

This will force metacity to be the windowmanager.  The user can still make changes for the individual session, but it will reset to the default when they log back in.  If you want to do this on an individual user basis you should be able to put that line in ~/.xsession.  For me though I wanted it on a system-wide basis.

---

