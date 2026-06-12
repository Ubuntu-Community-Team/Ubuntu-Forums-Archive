---
title: "apt want's to use proxy even when i disable it"
date: 2008-12-18
forum: General Help
---

### Post by outlaws42 on 2008-12-18
I am running Ubuntu 8.10 on my Dell 1420 laptop. when i connect to the internet at home I use a proxy. This part works fine when i do ```
sudo apt-get update
```. But when i go any where else and connect directly to the internet apt still wants to use my proxy. I have even tried to delete my apt.conf file all together and it still tries to connect through my proxy.  my apt.conf when i disable the proxy is as follows

```

#ACQUIRE
 {
  http
 {
    Proxy "http://192.168.0.6:8000/";
  };
 };
```

Just a note that everything else connects fine it's only apt that tries to use my proxy no matter what my settings.

---

### Post by bigbrovar on 2008-12-18
well am not sure about your method of enabling proxy for apt. we use proxy here to and what i do is add my proxy settings to ```
.bashrc 
```in my home directory and ```
bash.bashrc
``` in /etc i add the following to the bottom of both file so there look like this

```
    . /etc/bash_completion
fi

# Networkproxy
export http_proxy=http://proxy.aust-abuja.org:3128/

```

this works fine with every command i run that needs internet connecting would use my proxy. e.g wget,youtude-dl,apt-get, everything would be directed to use my proxy. to connect to the internet. and when am in a another network that dont need proxy to connect to the internet. all i do is add a comment to the proxy settings so that it becomes


```
    . /etc/bash_completion
fi

# Networkproxy
#export http_proxy=http://proxy.aust-abuja.org:3128/

```


i do this to both **/etc/bash.bashrc** and **$HOME/.bashrc**

so just ```
sudo gedit /etc/bash.bashrc 
```

and in your case it add 


```
export http_proxy=http://192.168.0.6:8000/
```

to the end of the file.

then do the same for 

.bashrc in your home dir

```
nano $HOME/.bashrc
```

AND ADD 

```
export http_proxy=http://192.168.0.6:8000/
```

to the end of the file.

so i would advise you undo the the proxy settings you have for apt.conf..


edit .. funny before posting this i just decided to check my /etc/apt/apt.conf file and i saw that my proxy settings had been automatically updated to it ..

cquire::http::proxy "http://proxy.aust-abuja.org:3128/";
Acquire::ftp::proxy "ftp://proxy.aust-abuja.org:3128/";
Acquire::https::proxy "https://proxy.aust-abuja.org:3128/";

am sure it was because i set synaptic to download thru my proxy.

you can go to synaptic > settings > preference > network and tell it to download directly from the internet. let me know if it works.

---

### Post by outlaws42 on 2008-12-18
I want to keep apt from using the proxy (unless i specify). is there a place that tells apt what a direct connection is? because I don't have my settings set to use a proxy right now that i can see, but apt wants to connect through it. I don't know where it's getting the settings.  I looked in .bashrc and /etc/wgetrc /etc/bash.bashrc none of them have proxy settings in them.  I even deleted my /etc/apt/apt.conf and still tries to connect through the proxy.

---

### Post by outlaws42 on 2008-12-18
working fine now not sure what's different but its working. bigbrovar thanks for your reply

---

