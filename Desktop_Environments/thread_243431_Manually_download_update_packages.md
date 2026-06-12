---
title: "Manually download update packages"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Saxphile on 2006-08-25
Hi,

I have an Ubuntu workstation set up at school, which charges me 17 cents for every MB I download. As a result, I haven't been updating it for months. I have a DSL connection at home, but taking the tower me with me is not only too much work but also unfeasible because I don't technically own the computer.

My question is this: Is there an easy way for me to export the list of packages to be updated from Synaptic, download them at home, and install them  in a reasonably easy manner? Also, as I have a variety of non-Ubuntu packages to be updated, just getting an updated ISO would only solve part of the problem.

Thanks for any advice.

---

### Post by vavoem on 2006-08-25
That would be a rather difficult thing to do.
Due to the fact your machine downloads only the packages on your computer wich need updating you'll have to set up a machine a like at your fast internet connection.

You might want to take a look at this pdf it's about apt-cacher

[http://www.oreilly.com/catalog/ubuntuhks/chapter/hack61.pdf#search=%22apt%20updates%20download%20once%20install%20many%20ubuntu%22](http://www.oreilly.com/catalog/ubuntuhks/chapter/hack61.pdf#search=%22apt%20updates%20download%20once%20install%20many%20ubuntu%22)

---

### Post by Saxphile on 2006-08-25
Okay that does sound complicated. I don't think apt-cache is what I need though since I'm only try to maintain one machine. Thanks for the reply though.

I was thinking more along the line of parsing output from apt/Synaptic, fetch the packages, and somehow make Synaptic aware of the now local packages. Has anyone done something similar?

---

### Post by FuriousLettuce on 2006-08-25
You could run

```
sudo apt-get update
```

then use synaptic / update manager to suggest the updated packages (I can't remember how to do this, I'm not at my box at the moment).

Then you could download them on your computer - you could use wget, or search for the packages in synaptic, note the web address then use firefox to save them.

Finally, it's possible to make your own local repository on your computer - just google it.

---

### Post by nikhilk on 2006-08-25
When you do a sudo apt-get install <package-name> add the --print-uris switch to the command.

This is what it does-
Instead of fetching the files to install their URIs are printed. Each URI will have the path, the destination file name, the size and the expected md5 hash. Note that the file name to write to will not always match the file name on the remote site! This also works with the source and update commands. (From apt-get man page)
It is a good idea to first check the man pages of the concerned command :)

Using this URI you can get the package using your DSL connection. Then just copy it to the other machine and install it by 'sudo dpkg -i <package>.deb'.

---

