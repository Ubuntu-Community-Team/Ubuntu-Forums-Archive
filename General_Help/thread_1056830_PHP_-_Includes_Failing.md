---
title: "PHP - Includes Failing"
date: 2009-02-01
forum: General Help
---

### Post by adamcoppard on 2009-02-01
I have set up Apache, so that rather than /var/www being the site, /home/adam/public_html is. I then disabeled the /var/www as default site, and enabled the second /home path as the site called 'adam'. Everything was hunky dorey, and is running, but all of my PHP includes in my applications fail.
This is the specific error:
```

Warning: require_once(../sb-includes/config.php) [function.require-once]: failed to open stream: No such file or directory in /home/adam/public_html/simplyblog2/sb-classes/config.php on line 2

Fatal error: require_once() [function.require]: Failed opening required '../sb-includes/config.php' (include_path='.:/usr/share/php:/usr/share/pear') in /home/adam/public_html/simplyblog2/sb-classes/config.php on line 2

```

I know for a fact that all the files exist that are being referenced though! Sorry if this is a common problem, but it's just a little annoying as I thought I had everything set up!

---

### Post by adamcoppard on 2009-02-01
That was a bit of a bad description, and the problem now only presents itself whenever using ../ to go up one directory. I can do this:
[PHP]
require 'config.php';
[/PHP]
This:
[PHP]
require 'sb-classes/config.php';
[/PHP]
But not:
[PHP]
require '../sb-includes/config.php';
[/PHP]

It only presents itself when using the host method outlined above (the method above DOES NOT use userdir method, just twisting and changing apache2.conf in /etc/apache2/apache2.conf)

Thanks,

---

### Post by adamcoppard on 2009-02-01
Now, why this is failing is very beyond me! It even fails with the default configuration, and doing ../test.php will work, where as ../sb-includes/config.php won't!

---

### Post by Spherical on 2009-02-01
I always use the following for includes:

[PHP]include($_SERVER['DOCUMENT_ROOT']."/dir/filename.php")[/PHP]

Or something like that.
That way, it always goes to the root directory of your site (thus public/html/ or something like that)
And after that, you locate the file from that root directory. (note the first /!)

that way has never failed me...

---

