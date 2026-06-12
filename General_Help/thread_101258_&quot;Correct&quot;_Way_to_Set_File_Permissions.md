---
title: "&quot;Correct&quot; Way to Set File Permissions?"
date: 2005-12-09
forum: General Help
---

### Post by bakert on 2005-12-09
Hi there,

I have set up Ubuntu as a web server.  Files for the website live under /var/www as per the default Apache config.

I now want to be able to edit my website from a client on the LAN.  This client can attach using a Samba share but obviously doesn't attach to the Ubuntu machine as root or www-data (current owner of the files).

So my question is, how do I make those files/directories under /var/www editable by the remote user?  I can just chmod 777 all the way down the tree but I DON'T want to do that!  I want to do it the right way.

What's The Right Way?

Thanks, Tom

---

### Post by ember on 2005-12-09
You can setup UserDir, which allows you to have a public_html-directory in your home directory. There you can edit files and view them with the webserver. Just comment out the option in the apache2.conf and restart apache.

Best,
ember

---

### Post by bakert on 2005-12-09
Hmmm ... could do that.

But really I want the remote user (me!) to be able to edit anything on the whole site.  So I'd have to move the whole site (1GB?) under my home directory.  That doesn't seem right somehow.

Is there another way?

Thanks, Tom

---

### Post by steve.horsley on 2005-12-09
I don't know if it is the "right" way, but I could be inclined to chgrp the whole tree to belong to my group. Or create a webedit group, chgrp the web tree to that and make all relevant users belong to the webedit group.

---

### Post by bakert on 2005-12-09
RIght, yes, that sounds the kind of solution I need!

But then www-data won't be able to write cache files and things like that.  So I'll have to make him a member of this new group too, right?

Is this a suitably Unix-y answer to my problem?

Thanks for your help!  Tom

---

### Post by bakert on 2005-12-09
Hmmm ... but then www-data will have write access to the whole website.  Is that desirable?

The PHP library I am using to grab some RSS writes cache files and that happens as the www-data user.

So what would be the solution there?  Not put the www-data user in the "web editors"
 group?  And then how does it write the cache files?  By moving the cache somewhere else and making that folder only writeable by www-data?  And how does www-data get write permissions on that folder?  By making him the owner?  Or putting him in some other group and giving group write access to that folder?

This files-only-belonging-to-one group is twisting my melon!  What's the standard practice?

Thanks, Tom

---

