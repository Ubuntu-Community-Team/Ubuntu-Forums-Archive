---
title: "unity boot option, message file location?"
date: 2012-09-30
forum: Desktop Environments
---

### Post by aaron.kyle on 2012-09-30
I am using Ubuntu 12.04.  I accidentally changed the user and group of my root file system the other day.  After I set it back, one lingering problem is that the text for the boot options (restart, shutdown, log out) is not rendering:

[IMG]http://www.flickr.com/photos/aaronkyle/8038262007[/IMG]

(that image link isn't working - the file is visible on flickr : [http://www.flickr.com/photos/aaronkyle/8038262007](http://www.flickr.com/photos/aaronkyle/8038262007))
 
I suspect this is just another permission thing, but I don't know where that file is stored to check.  Could anyone help to point me in the right direction?

Thanks in advance!

- Aaron

---

### Post by aaron.kyle on 2012-10-01
UPDATE:

I have continued to dig around.  I finally found this thread:

[http://ubuntuforums.org/archive/index.php/t-1551669.html](http://ubuntuforums.org/archive/index.php/t-1551669.html)

When I look at /usr/lib/indicator-session/gtk-logout-helper I see a bunch a characters (not written in human-readable format).  The thread linked above suggests that I should be looking for a zenity script, but I haven't yet figured out where I should be looking.

As a bit of additional information, that dialog box for shutdown appears fine for all my users; it just doesn't render when trying to shutdown when i am not logged in (e.g. prior to logging into an account).

I'd really appreciate some further guidance!

Thanks to all who are reading this.

- Aaron

---

