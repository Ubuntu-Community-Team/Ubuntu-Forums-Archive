---
title: "0 AD in Ubuntu 11.04"
date: 2012-06-15
forum: Gaming &amp; Leisure
---

### Post by MarjaE on 2012-06-15
My brother suggested this. I figured I would install it now and play it once my arms heal. I still can't get it to install. I tried using the download from SourceForge and I tried using the directions from here:

[http://trac.wildfiregames.com/wiki/LatestReleaseLinux](http://trac.wildfiregames.com/wiki/LatestReleaseLinux)

But those instructions are for 12.04 and maybe that's why they don't work with 11.04.

---

### Post by sffvba[e0rt on 2012-06-15
*Post moved to **own **Thread.*


404

---

### Post by ubuntu27 on 2012-06-15
Did you try the following in the [Terminal]("http://www.psychocats.net/ubuntu/terminal")? 

```
sudo add-apt-repository ppa:wfg/0ad
```
```
sudo apt-get update && sudo apt-get install 0ad
```

-----------------------

**EDIT:** Maybe the "add-apt-repository" tool does not exist in Ubuntu 11.04. If so, we have to do this manually.

1) Open Synaptic Package Manager

2) Click on Settings menu--->Repositories

3) A new window will open. 
Go to **Other Software** tab,

4) Click on "Add...", and then copy and paste 

```
deb http://ppa.launchpad.net/wfg/0ad/ubuntu natty main 
```, press ENTER or click on "Add"

5) Open a text editor such as gedit, and copy and paste the following> 
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ETGhMoQEEALgluYbrVJNrTU1mGh+x1ZxHIPd7NnrynYDXKfP7BM6qkIHTL1c0/tQwXpsS
9Y7rJc9MV05dd0Ew661INCMSQ3EQF6X+FnpZb9scZrZUv9YRiN9CGip3utm6SxRIwBlBtTU1
5tHv/lMSPJ4/RznYdEaWAb8h2dOppakIKcHGL58dABEBAAG0EExhdW5jaHBhZCAwIEEuRC6I
tgQTAQIAIAUCTGhMoQIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJEIynpujk+pU6EQ0D
/3qnpyOZvvbqekFxDevi4zcV0/kdN8DYzxP8AB2LvZRr0Mc2O5gcphHQ5COC3L8yhCV7VfmL
nJAK8VPSAuqC5ZOpwVgRq1hMXj+YGo7OoyBEGA5Px9fSXCM2Qf/3uIKLRVq/4AzhIKyfaNrC
o/HuAsiAPwOxnjL8VohXDM3eFUWU
=YT1J
-----END PGP PUBLIC KEY BLOCK-----

6) saved the text file as what-ever-name**.key**  [Make sure that it says **POINT key**]

7) Back to Synaptic Package Manager's Software Sources again.

Go to **Authentication** Tab

8) Click on Import Key file...

9) Open the file the you saved in step 6.

10) Close Software Sources

11) Open the Terminal and type (or copy and paste)

```
sudo apt-get update && sudo apt-get install 0ad
```

12) Enjoy the game



NOTE: For everyone else reading this, this steps by steps explanation is for Ubuntu 11.04. For any other version, just substitute the correct URL for your Ubuntu version in **step 4**.

The address can be found here: [https://launchpad.net/~wfg/+archive/0ad](https://launchpad.net/~wfg/+archive/0ad)

Just click on "Technical details about this PPA", and then select your Ubuntu version.

---

### Post by MarjaE on 2012-06-16
Thanks! It seems to have installed. I haven't tried it yet.

---

