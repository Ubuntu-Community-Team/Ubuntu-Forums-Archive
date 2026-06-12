---
title: "localhost display"
date: 2011-02-27
forum: Desktop Environments
---

### Post by reddae on 2011-02-27
So I realize that this is just about pointless, but this is simply out of curiosity.

When I point my browser to [http://localhost/](http://localhost/) it displays:
**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.




Is there any way to actually put content on this? For instance if I wanted to make [http://localhost/](http://localhost/) the default page in Firefox and have some kind of functionality to it, would that be possible?

---

### Post by AlfredVargas on 2011-02-27
that's possible for all i know. all you have to do is to find the file and edit. it is usually found in htdocs.

---

### Post by SeijiSensei on 2011-02-27
On Debian/Ubuntu, the web content is stored in the /var/www directory.  You'll find the default index.html there.

You'll have major permission issues if you try to put files there as an ordinary user because the directory is owned by the "www-data" user that Apache runs as.  There are solutions, like adding your username to the "www-data" group.  Do a little searching here and on Google for details.

---

