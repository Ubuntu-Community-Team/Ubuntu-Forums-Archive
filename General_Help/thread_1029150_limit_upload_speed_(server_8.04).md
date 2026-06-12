---
title: "limit upload speed (server 8.04)"
date: 2009-01-03
forum: General Help
---

### Post by rascalli on 2009-01-03
I have a nice server , that I share with some people.
We should all use some speed , but as you can imagen ofcourse some go over it ;-/

So I am looking at shaping the traffic on the specific ports

I use torrentflux as client & all users will have there own ports
user A has : 50000 - 50300 and can use 25mbit as speed
B 50400-50600 and can use 15mbit as speed
and so on

I tried to use this script : 

[http://www.torrentflux.com/forum/index.php/topic,2206.msg17158.html#msg17158](http://www.torrentflux.com/forum/index.php/topic,2206.msg17158.html#msg17158)

but I am getting the following error when starting it with : /etc/init.d/script.sh start (also sudo did not help)

root@XXXXX:~# sudo /etc/init.d/test.sh start
Starting bandwidth shaping: RTNETLINK answers: No such file or directory
RTNETLINK answers: No such file or directory
RTNETLINK answers: No such file or directory
RTNETLINK answers: No such file or directory
RTNETLINK answers: No such file or directory
RTNETLINK answers: No such file or directory
RTNETLINK answers: Operation not supported
We have an error talking to the kernel
RTNETLINK answers: Operation not supported
We have an error talking to the kernel
done

any idea how to solve this ?

Or alternative another way to shape traffic per port ?

---

