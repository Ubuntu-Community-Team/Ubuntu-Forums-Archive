---
title: "[help]on line by proxy,but i cann't &quot;apt-get update&quot;"
date: 2005-12-17
forum: General Help
---

### Post by survival on 2005-12-17
[help]on line by proxy,but i cann't "apt-get update"
i  am now, use the mozilla on line by proxy,like this:
Edit/Preferences/General/Connection/Connection Settings..
 in the new box ,i choose  "Mannual proxy configuration " and "use the same proxy for all protocols" .blow this  ,there are several protocols like http,ssl,ftp,gophter. all of them use the same proxy ip address and port.

then  ,i want to update.so in a terminal, i do like this:
sudo - s -H
apt-get update
but can not connect to . so i think, now .although i go on line by the proxy:port .but this command "apt-get update " may not use this proxy:port as default port .so how can i do to deal with this problem..

waiting on line......thank you very much!!!!!
=========================================
this problem has been done perfectly. the details in the #4 below.

---

### Post by Leif on 2005-12-17
I don't know the solution to your problem, but a quick search shows that other people have asked the same question as you, so I suggest you read those threads : [http://ubuntuforums.org/search.php?searchid=2983731](http://ubuntuforums.org/search.php?searchid=2983731). good luck !

---

### Post by survival on 2005-12-17
thank you .i go to ,right now

---

### Post by survival on 2005-12-17
done!

in a terminal,i do like this:
sudo -s -H
export http_proxy=http://x.x.x.x:nnnn
apt-get update

then, everything goes very well!

---

### Post by sunny_nwho on 2005-12-17
I think if you add a proxy specification in ur apt.conf file it will also be ok...it worked for me. I did the following

sudo gedit /etc/apt/apt.conf

add the follwoing lines

Acquire {
    Retries "0";
    Http {
        Proxy "http://username: password@host: port/";
    }
};

if ur proxy uses authentication like mine u might want to specify ur username and password if not u can directly type the host name either in IP form or webaddress form and the port.

---

