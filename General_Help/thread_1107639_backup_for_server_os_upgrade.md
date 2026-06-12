---
title: "backup for server os upgrade"
date: 2009-03-27
forum: General Help
---

### Post by Linux&amp;Gsus on 2009-03-27
I'm about to upgrade my server OS. While I don't expect anything dramatically going wrong I still would like to play safe and backup the relevant (config) files first.

Not being a server expert I thought I better ask first. So, what would be the directories (besides /home) I need to backup? Just in case something does go wrong and I need to re-install. I just don't want to set up DNS, DHCP, Users, etc, again. Which I, embarrassing to say so, configured via Webmin.

Thanks for your help.

---

### Post by neilevan814 on 2009-03-27
Well, I will add to your /home, /etc/apache2, and /etc/ssh for starters

---

### Post by Linux&amp;Gsus on 2009-03-27
Thanks, so basically I'll just grab /etc.
Are there any other config files hidden somewhere else?

---

### Post by neilevan814 on 2009-03-27
I'm surprised no one else has responded and I am not that old to the server configuration set up myself, but I believe if you gather up /etc that is where they all are.  

Anyone else??????

---

### Post by lykwydchykyn on 2009-03-28
I typically just tar up the whole / partition.  On a server install, it's usually not more than a few hundred MB compressed.  That way if I need to go back, I don't have to mess with reinstalling and then rebuilding everything, I just slick the root partition and drop the tarball back on there.

---

### Post by neilevan814 on 2009-03-28
yeah...better safe than sorry....I was just gonna add /var/log/apache2 for all your error and access reports...

---

### Post by Linux&amp;Gsus on 2009-03-29
Thanks for the suggestions, guys.
However, I might have blown it already... ](*,) :cry:

See here:
[http://ubuntuforums.org/showthread.php?t=1108660]("http://ubuntuforums.org/showthread.php?t=1108660")

Any help would be appreciated.

Cheers,
L&G

---

### Post by hyper_ch on 2009-03-29
there's also stuffin /var (e.g. /var/www or /var/lib/mysql)...

---

