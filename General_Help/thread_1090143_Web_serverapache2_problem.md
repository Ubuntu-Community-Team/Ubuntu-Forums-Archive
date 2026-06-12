---
title: "Web server/apache2 problem"
date: 2009-03-07
forum: General Help
---

### Post by Kal318 on 2009-03-07
I'm currently having a problem getting images to appear on my web site from my web server running Ubuntu 7.10 and apache2. I found that a

"chmod 777 /my/image/location/"
followed by a
"chmod 644 /my/image/location/*"

solves this problem temporarily. Until i add new images to the image directory. After which I would need to redo the chmod commands. This is a big problem every time I publish changes to my server. I'm sure there's a way to solve this. But I'm still very noob when it comes down to linux.

---

### Post by beno1990 on 2009-03-08
Are you adding the files manually or uploading them through a script on the webserver?

If you are uploading them manually, simply type

```

umask 777

```

(replace 777 with whatever permissions you want) and any files/folders you create from then on during that bash session will have those permissions you chose in the umask.

Also, it's better practice to change the files you're uploading to your webserver to the webserver's group or change the ownership to the webserver.

To do that:

```

chown -R www-data /your/webserver/directory

```

or:

```

chgrp -R www-data /your/webserver/directory

```

The -R command means recursive, and applies the command to all files in any directory below it. It works for chmod, too.

---

