---
title: "Pidgin 2.5.1 can't connect to Yahoo server"
date: 2008-09-24
forum: Desktop Environments
---

### Post by syn4k on 2008-09-24
I'm using Pidgin 2.5.1

**My advanced settings are:**
pager server: scs.msg.yahoo.com
japan pager server: cs.yahoo.co.jp
pager port: 5050
file transfer server: filetransfer.msg.yahoo.com
japan file transfer server: filetransfer.msg.yahoo.co.jp
file transfer port: 80
chat room locale: us
encoding: ISO-8859-1
proxy type: use gnome proxy settings

**My basic settings are:**
protocol: yahoo
username: syn4k
password: somepass

**How I installed:**
# Pidgin dependencies installation
echo "Installing Pidgin..."
sudo apt-get -yqq build-dep pidgin
sudo apt-get -yqq install network-manager-dev

# Pidgin download and installation
wget -q [http://downloads.sourceforge.net/pidgin/pidgin-2.5.1.tar.bz2](http://downloads.sourceforge.net/pidgin/pidgin-2.5.1.tar.bz2)
tar -xvf pidgin-2.5.1.tar.bz2
sudo apt-get -yqq remove pidgin libpurple0
cd pidgin-2.5.1/
./configure -enable-gnutls=yes
make
sudo make install
cd ..
rm -rf pidgin-2.5.1/
rm -rf pidgin-2.5.1.tar.bz2

# Pidgin notifications installation
sudo apt-get -yqq install pidgin-libnotify

**Error:** Could not establish a connection with the server:
Network is unreachable

---

### Post by sub_par11 on 2008-09-27
Probably shouldn't post your password on here.

---

### Post by starscalling on 2008-10-24
66.163.181.173 scs.msg.yahoo.com 
put that in /etc/hosts file and good to go from here.. try doing a ping on scs.msg.yahoo.com and put that resulting ip in instead. for me cleared up ever since.

---

### Post by Drate on 2008-11-20
I can confirm it works!

---

### Post by stucky on 2008-11-20
Can also confirm this works in Lenny:guitar:

---

### Post by Syndacate on 2009-04-22
I can also confirm that it works in the following, as I had this issue on both:
- Windows XP Professional SP3
- Ubuntu Linux (8.10, Intrepid Ibex)

Just took the resulting IP from a ping and put that into the server to connect to instead of its DNS.

---

### Post by chrone on 2009-05-18
thanks dude, it works. :)

---

### Post by ynov on 2009-06-22
thanks starcalling,
it works for any [email]xxx@yahoo.com[/email] account,
:D

---

### Post by alexrose on 2009-06-24
works now .. I've updated to 2.5.7 :D

---

### Post by mastapat11 on 2009-07-04
you could also try the easier solution:
[I][http://ubuntuforums.org/showthread.php?t=1191064]("http://ubuntuforums.org/showthread.php?t=1191064")
[/I]

changed the server
***scs.msg.yahoo.com***
to
**cn.scs.msg.yahoo.com**

---

### Post by hafthanhf on 2009-07-29
My Pidgin is not working properly. I can chat with it but, I can't receive or send file by using it. How can I resolve this problem.

---

### Post by asif_1088119 on 2009-09-23
> **starscalling said:**
> 66.163.181.173 scs.msg.yahoo.com 
put that in /etc/hosts file and good to go from here.. try doing a ping on scs.msg.yahoo.com and put that resulting ip in instead. for me cleared up ever since.

should i write ''66.163.181.173 scs.msg.yahoo.com''on top of hosts file?how to ping?what does that sentence '' put that resulting ip in instead. for me cleared up ever since''mean?

---

### Post by ovidiub on 2009-09-23
Go to: [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

Add the repo. Update pidgin. Problem solved.

Good luck!

---

### Post by udinahmad on 2009-12-19
try this
server : cn.scs.msg.yahoo.com
port : 5050
file transfer : filetransfer.msg.yahoo.com
port : 80

---

### Post by hafthanhf on 2009-12-19
thanks you guys, everything now go well

---

