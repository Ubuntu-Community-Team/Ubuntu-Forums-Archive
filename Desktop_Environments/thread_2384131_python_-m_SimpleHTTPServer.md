---
title: "python -m SimpleHTTPServer"
date: 2018-02-02
forum: Desktop Environments
---

### Post by Geoff_Lane on 2018-02-02
Folks,

Not sure if this should be under the 'network' heading or not but I'm sure it'll be moved if appropriate.

I've used this before to transfer files between two remote machines using wget but the wget -c option does not resume the transfer, it starts right from the beginning again.

I've used wget with the -c option on numerous occasions getting a file from an apache server but it's not working using the python -m SimpleHTTPServer option.

Appreciate SimpleHTTPServer is a very simple server but thought it was the wget -c that resumed and not to do with the server.

Geffers

---

### Post by spjackson on 2018-02-03
It is to do with the server as well. wget can only ask the remote server to start from a certain point in the file if the remote server supports such a request. I've never used python -m SimpleHTTPServer but your experience suggest that it does not provide this function.

---

### Post by Geoff_Lane on 2018-02-03
> **spjackson said:**
> It is to do with the server as well. wget can only ask the remote server to start from a certain point in the file if the remote server supports such a request. I've never used python -m SimpleHTTPServer but your experience suggest that it does not provide this function.

Thanks for reply, suppose it had to be really.

wget so easy for transferring files and resuming if connection breaks. scp OK provided connection doesn't fail. rsync can get complicated.

Thanks for reply.

Geffers

---

