---
title: "Creating a Subversion repository"
date: 2006-12-22
forum: Desktop Environments
---

### Post by boralyl on 2006-12-22
I'm having some difficulty importing my files into my newly created subversion repository.  I've installed and configured apache2 and both of the following:

```
sudo apt-get install subversion
sudo apt-get install libapache2-svn
```

I've edited /etc/apache2/mods-available/dav_svn.conf uncommenting:
```

DAV svn

SVNParentPath /var/svn

AuthType Basic
AuthName "Subversion Repository"
AuthUserFile /etc/apache2/dav_svn.passwd

```

I then restarted apache and created the repository via:
```

sudo mkdir /var/svn
sudo svnadmin create /var/svn

```

Then gave apache ownership..
```

sudo chown -R www-data:www-data /var/svn

```

Then added a user
```

sudo htpasswd2 -c /etc/apache2/dav_svn.passwd theusername

```

The problem arises when I try to import my project.  This is the code I used:
```

svn import /var/www/site http://localhost/svn/site -m "creating repository" --username theusername --password mypassword

```

I receive this error:
```

svn: PROPFIND request failed on '/svn/site'
svn: Could not open the requested SVN filesystem

```

This sounds like a permissions problem, but I am at lost at where to go next, any ideas?

---

