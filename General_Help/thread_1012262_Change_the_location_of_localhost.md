---
title: "Change the location of localhost"
date: 2008-12-15
forum: General Help
---

### Post by vedran.omeragic on 2008-12-15
Hi,
About, apache and web servers... I'd like to know, how can I change the current default localhost folder that can be found under */var/www/* to some other folder, of my own choice...

---

### Post by hikaricore on 2008-12-15
I could be a little off here but this should be close.

> sudo gedit /etc/apache2/sites-enabled/000-default

>         DocumentRoot **/var/www/**
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory **/var/www/**>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>


Change the bolded sections, save, and restart apache.

> sudo /etc/init.d/apache2 restart

---

### Post by Coreigh on 2008-12-15
EDIT: hikaricore points out that the file is in 'sites-enabled'. On my web server the 'sites-enabled/000-default' is a link to 'sites-available/default'. So edit whichever file is real and not a link.


OriginalPost:
In the file /etc/apache2/sites-available/default find the line:

DocumentRoot /var/www

Comment it out (don't delete it)

# DocumentRoot /var/www

And add your desired location

DocumentRoot /Path/to/My-www-folder


Beware of the need to use correct ownership and permissions to allow Apache to serve pages. I know mine are usually messed up or not secure enough, but I have a private intranet. You can view the default folder permissions by typing this in a terminal window ```
ls -l /var/www
```

---

### Post by spiderbatdad on 2008-12-15
you can easily use the virtual hosts file /etc/apache2/sites-available.
Copy the file called "default" to one called "my-site" (for example.)
Then edit that file to suit your desires. So you might point to /home/user/www instead of /var/www
When you are ready to use the new site:```
sudo a2dissite default && sudo a2ensite my-site
sudo /etc/init.d/apache2 restart
```

Edit: lol I'm too slow. Any of the above will work too.

---

### Post by vedran.omeragic on 2008-12-15
Thank you guys, hikaricore's solution worked fine for me...

---

