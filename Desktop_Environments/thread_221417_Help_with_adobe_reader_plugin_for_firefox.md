---
title: "Help with adobe reader plugin for firefox"
date: 2006-07-23
forum: Desktop Environments
---

### Post by electroconvulsive on 2006-07-23
I need help getting the adobe reader plugin for firefox working. I have downloaded and installed the adobe reader from the adobe website as the one from the repos does not have a browser plugin. I have succesfully installed the reader and got it working. I have installed the plugin as according to the instructions given by running the install script supplied with the reader. and made sure that nnpdf.so was copied to /usr/lib/firefox/plugins. This is where I get stuck because after restarting my browser pdf files still dont open in the browser and when I check about:plugins the adobe reader plugin doesnt show up. The final line of the install instructions is as follows. 

[COLOR="Red"]After the installation succeeds, please make sure that the
acroread startup script is in the PATH environment variable.[/COLOR]

I dont know what thios exactly means and much to my lament google, these forums and the ubuntu wiki do not have an answer for it either. So if anyone can either tell me what this means and how to acheive it I will appreciate it very much.

---

### Post by rudiz on 2006-07-23
sudo apt-get install acroread mozilla-acroread acroread-plugins

---

### Post by philippe_carlo on 2006-07-23
(1) Open up a terminal.
(2) type 'which acroread'
(3) if there is output (like /usr/bin/acroread) then you're fine
    else you have to mess around as follows.

(a) The PATH variable contains all directories with binaries on your system, so that when you run a command, instead of having to type the entire path to the binary, it searches those directories for an executable with the same name. Adding the directory containg acroread to this list, makes it accessible for - among others - the firefox plugin.
To do this:
(b) Open up a terminal and do 
```
gedit ~/.bashrc
```
(c) at the end add the following
```
export PATH=$PATH:<path_to_acroread>
```
replace <path_to_acroread> with the appropriate value.

Log out and in again, and you should be fine.

---

### Post by electroconvulsive on 2006-07-23
Thanks for your help, but even though now the path points to the folder of the adobe reader plugin in my root and my user account pdfs do not show up in my browser nor does the plugin show up in my about:plugins directory either and to add to that I even tried associating the download value for pdf files to the actual plugin to see if that would work. Now I cant undo the fil assocoations so pdfs dont show up at all. The Firefox panel >edit>preferences>downloads> does not display the file association I just made at all so I cant change it back to what it was originally. Even though it is supposed to.

---

### Post by electroconvulsive on 2006-07-23
x

---

### Post by electroconvulsive on 2006-07-25
> **rudiz said:**
> sudo apt-get install acroread mozilla-acroread acroread-plugins

This only works for mozilla browser and if you try to copy the link to the firefox plugin folder it doesnt work.

---

### Post by philippe_carlo on 2006-07-25
Something seems to be very 'off'. May you should try reinstalling firefox:
```

sudo aptitude reinstall firefox

```

Maybe the following also helps:
```
sudo apt-get install mozilla-firefox
```

---

### Post by electroconvulsive on 2006-07-25
> **philippe_carlo said:**
> Something seems to be very 'off'. May you should try reinstalling firefox:
```

sudo aptitude reinstall firefox

```

Maybe the following also helps:
```
sudo apt-get install mozilla-firefox
```

Yeah thanks dud I actually solved the problem I had with file associations by deleting /etc/firefox/profile/mimeTypes.rdf and restarting the app. Im going to try to reinstall firefox but does that mean that I will have to reinstall all the plugins or should I back up the plugin folder and restore the contents after reinstalling?

---

