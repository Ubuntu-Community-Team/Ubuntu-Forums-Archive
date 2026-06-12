---
title: "Serving apache from home...?"
date: 2021-09-21
forum: Desktop Environments
---

### Post by dbee on 2021-09-21
What's the easiest way to do this? 

I could enable user_dir on apache. But i want to be able to control the directory path.

I need to create a symlink from somewhere to somewhere?

Can't find the answer anywhere...

Maybe /var/www/mysite to /etc/apache2/sites-enabled?

can someone help me out here?

---

### Post by ActionParsnip on 2021-09-21
If the data is in your home folder you will need to make sure that the apache user has at least read access to the data, could get messy

---

### Post by dbee on 2021-09-21
What's the best way to integrate localhost with local git then?

Maybe move the git repo to /var/www/ ?

---

### Post by Holger_Gehrke on 2021-09-21
'/etc/apache2/sites-enabled/' is a directory full of symbolic links to configuration files stored in '/etc/apache2/sites-available/'. So you basically create a configuration for your site in sites-available and activate it by linking it into sites-enabled. You normally use a2ensite to do this linking.

You can give a different name for the directory to be used for the userdir in /etc/apache2/mod-available/userdir.conf by replacing 'public_html' with a directory name of your choice (remember to change both occurrences, the one after UserDir (line 2 on my system) and the one in the Directory line (line 5 ...).

The configuration language for apache is very expressive but also quite complex. I urge you to try to read the documentation at [http://httpd.apache.org/docs/2.4/]("http://http://httpd.apache.org/docs/2.4/") .

Holger

---

### Post by mIk3_08 on 2021-09-21
> **dbee said:**
> What's the easiest way to do this? 
I could enable user_dir on apache. But i want to be able to control the directory path.
I need to create a symlink from somewhere to somewhere?
Can't find the answer anywhere...

Maybe /var/www/mysite to /etc/apache2/sites-enabled?

can someone help me out here?

I don't really get you but if you where about to change location
you should declare it to your configuration:
ex.

location /{
root /etc/apache2/sites
index index.html
}

this should be in the server side configurations.

---

