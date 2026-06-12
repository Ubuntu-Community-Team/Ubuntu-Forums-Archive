---
title: "How to switch library version"
date: 2009-01-11
forum: General Help
---

### Post by antubis on 2009-01-11
Hello,

Here is my problem. I've installed a subversion from source but then I decide to install it from package. Everything working fine ( from Windows there are no problems to connect with tortoise via WebDAV ) but I wanted to use a WebSVN. It use the command line to communicate with SVN and it gives me this error: Unrecognized URL scheme for. So after some googling I found the problem - I have two runing versions of svn lib.

bash: type -a svn
svn is /usr/local/bin/svn
svn is /usr/bin/svn
svn is /usr/bin/X11/svn

bash: which svn
/usr/local/bin/svn

/usr/local/bin/svn should be the compiled from source version. So how can I switch it to /usr/bin/svn?

Cheers

---

