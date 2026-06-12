---
title: "iTalc errors (ISD-server)- please help!"
date: 2009-06-05
forum: General Help
---

### Post by gforster on 2009-06-05
I have installed iTalc through our lab. Now I am getting weird errors. At first i thought is was an issue authenticating the key, but I have fixed that. I am getting the following error from the client computers when I try and connect to them:

The ISD-server could not be started because port 5800 is already in use. Please make sure that no other application is using this port and try again.

So, I checked what was using port 5800 and found it to be ica. ica is the iTalc client! It is what is supposed to be running on port 5800! Why would it give me an error? This is ridiculous. 

Setting up this program is the one thing I have come across that is immensely easier on windows. It seriously took me all of 10 minutes to set up this program when it was a windows lab. 

There is little up-to-date documentation or guides. The newest I have found is someone running 8.04 and running iTalc version 1.06. I am running 9.04 and version 1.09. 

What am I missing here? I have tested on the master computer using localhost and it works just fine.

My italc_client.log says:
Fri Jun 5 16:43:38 2009: [critical] isdServer::isdServer(...): could not start ISD server: The bound address is already in use
Fri Jun 5 16:43:38 2009: [warning] The ISD-server could not be started because port 5800 is already in use. Please make sure that no other application is using this port and try again.

---

