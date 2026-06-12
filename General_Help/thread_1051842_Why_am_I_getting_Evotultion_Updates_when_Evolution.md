---
title: "Why am I getting Evotultion Updates when Evolution is removed?"
date: 2009-01-27
forum: General Help
---

### Post by Donalb on 2009-01-27
Hey all, 
I use Thunderbird all the time. When I started on Ubuntu a year ago, I had problems setting evolution up with gmail, which made me switch completely to T'Bird with Lightning. So I completely removed all Evolution, but still, every so often (like today) a bunch of Evolution updates come through the update manager. 
If I choose not to install them, they keep getting offered. What am I not understanding here? (I know it'll be me)

regards

---

### Post by glennzo on 2009-01-27
> **Donalb said:**
> Hey all, 
I use Thunderbird all the time. When I started on Ubuntu a year ago, I had problems setting evolution up with gmail, which made me switch completely to T'Bird with Lightning. So I completely removed all Evolution, but still, every so often (like today) a bunch of Evolution updates come through the update manager. 
If I choose not to install them, they keep getting offered. What am I not understanding here? (I know it'll be me)

regards

Hi Donalb. I am a Fedora user dabbling in Ubuntu so I don't know a lot about the Ubuntu update process yet. What I would like to note is that with Fedora / YUM I can edit my yum.conf file to "exclude" certain packages so that they won't even be considered during any yum operations. As a matter of fact I exclude evolution* on two of my Fedora systems as I don't retrieve e-mail on those systems. I'm wondering, and suggets that there may be a similar option for the Ubuntu update system?

---

### Post by nikgare on 2009-01-27
You probably have not completely removed evolution from your computer.

Please post the output of this:

**sudo aptitude search evolution**

---

### Post by Donalb on 2009-01-27
Cheers. Here's the results below. I had removed Evolution though Synaptic, I thought that was sufficient. Granted, I didn't go back and check. Now that I do I see there's still stuff in there such as evolution-data-server_common which, if I select that for complete removal , seem to affect too many other things eg Ubuntu desktop, applets etc also marked for removal?


p   b2evolution                     - multilingual, multiuser, multi-blog engine
p   beagle-backend-evolution        - evolution data backend for beagle         
c   evolution                       - groupware suite with mail client and organ
i   evolution-common                - architecture independent files for Evoluti
i   evolution-data-server           - evolution database backend server         
i   evolution-data-server-common    - architecture independent files for Evoluti
p   evolution-data-server-dbg       - evolution database backend server with deb
p   evolution-data-server-dev       - Development files for evolution-data-serve
p   evolution-dbg                   - debugging symbols for Evolution           
p   evolution-dev                   - development library files for Evolution   
c   evolution-exchange              - Exchange plugin for the Evolution groupwar
p   evolution-exchange-dbg          - Exchange plugin for Evolution with debuggi
p   evolution-jescs                 - Evolution Connector for Sun Java Enterpris
p   evolution-plugins               - standard plugins for Evolution            
p   evolution-plugins-experimental  - experimental plugins for Evolution        
p   evolution-rss                   - Evolution RSS Reader Plugin               
i   evolution-webcal                - webcal: URL handler for GNOME and Evolutio
i A libevolution3.0-cil             - CLI bindings for Evolution                
p   libmultisync-plugin-evolution   - Ximian Evolution plugin for MultiSync     
p   librevolution-ruby              - Ruby binding for the Evolution mail client
p   librevolution-ruby1.8           - Ruby 1.8 binding for the Evolution mail cl
p   mail-notification-evolution     - evolution support for mail notification   
p   openoffice.org-evolution        - Evolution Addressbook support for OpenOffi
v   openoffice.org2-evolution       -                                           
p   opensync-plugin-evolution       - Evolution plugin for opensync

---

### Post by ray field on 2009-01-27
I am having the very same issue (similar output to "sudo aptitude search evolution" as well) -- and likewise, there are so many dependencies I hesitate to remove them completely -- especially when I come across something like
 
[http://www.stevey.eu/2008/08/removing-evolution-mail-is-not-dangerous-in-the-slightest/](http://www.stevey.eu/2008/08/removing-evolution-mail-is-not-dangerous-in-the-slightest/)

which isn't particularly reassuring, eg:

>There is enough explicit proof that the only package related to Evolution that depends on others that are still needed by the system is evolution-data-server-common there is no possible way that removing the others would harm your installation in any way whatsoever!

---

### Post by Bios Element on 2009-01-27
I suspect some requirements were bugged or something because It Tried to re-install evolution for an "Update" when I know for sure I removed it fully. Not exactly a major issue but I'm pretty sure something got bugged.

---

### Post by Gramps on 2009-01-27
> **Donalb said:**
> Cheers. Here's the results below. I had removed Evolution though Synaptic, I thought that was sufficient. Granted, I didn't go back and check. Now that I do I see there's still stuff in there such as evolution-data-server_common which, if I select that for complete removal , seem to affect too many other things eg Ubuntu desktop, applets etc also marked for removal?


Be careful here, I just did this yesterday thinking that I didn't use evolution so I didn't need it at all and I removed all I could find. Everything was fine until I rebooted then both taskbars were gone.

As it turns out gnome uses some some of evolution :( I had to get a terminal open and apt-get the gnome-panel

---

### Post by stchman on 2009-01-27
> **Donalb said:**
> Hey all, 
I use Thunderbird all the time. When I started on Ubuntu a year ago, I had problems setting evolution up with gmail, which made me switch completely to T'Bird with Lightning. So I completely removed all Evolution, but still, every so often (like today) a bunch of Evolution updates come through the update manager. 
If I choose not to install them, they keep getting offered. What am I not understanding here? (I know it'll be me)

regards

What method did you use to remove Evolution?  I always autoremove when removing apps.  The autoremove command removes all unused dependencies.

---

