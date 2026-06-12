---
title: "Update packages &quot;can't be authenticated&quot;?"
date: 2007-02-24
forum: Development CD/DVD Image Testing
---

### Post by lwc on 2007-02-24
Today I suddenly finds that all new packages (which are going to be downloaded from the internet) cannot be authenciated. So I am forced to abandon the updates.

The update function was okay yesterday. What happened?

(PS. install new software will also produce the same problem)

---

### Post by pochu on 2007-02-24
There was a problem with the archive, but it was fixed. I think the problem was with the gpg keys, but I'm not sure about that.

---

### Post by David Andersson on 2007-12-01
I had this problem in Ubuntu 7.10. This solved it for me:

```
sudo apt-get update
```

Then use the update manager as usual.

(Thanks to the commenter on this blog entry [http://linuxtnt.wordpress.com/2007/08/27/cant-be-authenticated-2]("http://http://linuxtnt.wordpress.com/2007/08/27/cant-be-authenticated-2"))

---

### Post by LENNYMANSELLmansell@gmail on 2011-03-09
FYI: I received the following error when executing apt-get update:



W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/maverick/Release](http://ubuntu.media.mit.edu/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/maverick-updates/Release](http://ubuntu.media.mit.edu/ubuntu/dists/maverick-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by slashwannabe94 on 2011-03-19
I recieved the same errors when trying to update one time. 

Running the following commands one after another fixed it. 

to run the commands, click on Applications then Accessories then terminal. copy and paste each command one by one into the terminal and press enter, if it prompts for your password then enter it and press enter. 

gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783  | sudo apt-key add -
gpg --keyserver keyserver.ubuntu.com --recv 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5  | sudo apt-key add -
sudo rm /var/lib/apt/lists/partial/*
sudo rm /var/lib/apt/lists/*
sudo apt-get update

---

### Post by rvjr on 2011-11-14
Good answer! Removing the contents of lists and lists/partial helped! Thanks!

---

