---
title: "Making a shell script"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Skerit on 2006-09-24
Because I'm quite the "heavy downloader" azureus often locks up because it reaches the 1024 open files limit. I found a nice workaround, but it's only to be used in a terminal and, even though I've fiddled around with gksudo, I can't get it to work properly ...

(I can't place a link in my menu and press it, my script also has to be run from a terminal)

The command I want to make a script for is:

sudo bash -c 'ulimit -n 8192; sudo -u skerit ./azureus'

---

### Post by Jose Catre-Vandis on 2006-09-24
Open up your text editor (gedit?) and add the following

#!/bin/bash
sudo bash -c 'ulimit -n 8192; sudo -u skerit ./azureus'

and save the file with your preferred filename (I used "myscript")

Should look something like this?
```
#!/bin/bash
sudo bash -c 'ulimit -n 8192; sudo -u skerit ./azureus'
```

Then you can run the script from terminal as follows:

```
./myscript
```

Well this works OK for me anyway :-)
Don't forget to make the script executable:
```
sudo chmod +x myscript
```

---

