---
title: "Can't Get Updates"
date: 2009-03-06
forum: General Help
---

### Post by zdunham on 2009-03-06
Hi, as of yesterday I am no longer able to get updates or any packages through terminal or through the update manager. It says it is unable to connect to [http://security.ubuntu.com/(whatever](http://security.ubuntu.com/(whatever) goes here). I am able to go to the Ubuntu website and type that URL in manually and it goes to the security page but for some reason the update manager and the terminal cannot. They were working 2 days ago perfectly fine. Any ideas? Thanks in advance.

---

### Post by cdenley on 2009-03-06
Try posting some output from commands that show your problem.
```

host security.ubuntu.com
nc -z -v security.ubuntu.com 80

```

---

### Post by zdunham on 2009-03-06
Here is what I get:

host security.ubuntu.com:

```

security.ubuntu.com has address 91.189.88.37

```

nc -z -v security.ubuntu.com 80:

```

DNS fwd/rev mismatch: security.ubuntu.com != auckland.canonical.com
security.ubuntu.com [91.189.88.37] 80 (www) open

```

Thanks for replying. I'm not a Linux expert either so this may not be that big of a problem whatever it is, I could just be missing something easy.

---

### Post by cdenley on 2009-03-06
Well, you just connected to the server from the terminal, so as far as I can tell from any output you posted, there is no problem.

---

### Post by zdunham on 2009-03-06
Alright here is what I get:

sudo apt-get update:

```

Err http://security.ubuntu.com intrepid-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com intrepid-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

```

That list goes on for awhile for whatever packages it couldn't get. I just ran that now too so it still isn't working. Thanks for help though.

---

### Post by abn91c on 2009-03-06
> **zdunham said:**
> Alright here is what I get:

sudo apt-get update:

```

Err http://security.ubuntu.com intrepid-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com intrepid-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

```

That list goes on for awhile for whatever packages it couldn't get. I just ran that now too so it still isn't working. Thanks for help though.
change to the Main or US servers

---

### Post by feelshift on 2009-03-06
Go to System > Administration > Software Sources and select Download from Main Server.

---

### Post by zdunham on 2009-03-06
> **feelshift said:**
> Go to System > Administration > Software Sources and select Download from Main Server.

It was on United States Server and I changed to Main Server and still go the same errors.


Thanks for replying.

---

### Post by cdenley on 2009-03-06
You're trying to use a proxy on localhost:4001, but the connection is refused. You probably don't have a proxy running on that port.
```

echo $http_proxy
sudo http_proxy= apt-get update

```
System>Preferences>Network Proxy

---

### Post by zdunham on 2009-03-06
> **cdenley said:**
> You're trying to use a proxy on localhost:4001, but the connection is refused. You probably don't have a proxy running on that port.
```

echo $http_proxy
sudo http_proxy= apt-get update

```
System>Preferences>Network Proxy

I'll try it tomorrow morning and post back, sounds good, thank you for the help. I'd try it now but it is Friday night and I am going out. Thanks again.

---

### Post by zdunham on 2009-03-07
> **cdenley said:**
> You're trying to use a proxy on localhost:4001, but the connection is refused. You probably don't have a proxy running on that port.
```

echo $http_proxy
sudo http_proxy= apt-get update

```
System>Preferences>Network Proxy

In Xubuntu there is no System>Preferences>Network Proxy.

I did what you had in the code section but nothing has changed.

---

### Post by zdunham on 2009-03-07
Alright I found the Network Proxy Preferences. 

It was in Accessories>AppFinder, Proxy Configuration is currently set to Direct Internet Connection and nothing else.

Now this seems odd but I could be wrong, in Ignored Hosts I have localhost, 127.0.0.0/8 and *.local. 

??

Thanks for the help.

---

### Post by zdunham on 2009-03-09
No more ideas?

---

### Post by cdenley on 2009-03-09
You need to change your proxy settings. I'm not sure how to do that in Xubuntu, but you're definitely trying to use an incorrect proxy.

---

### Post by zdunham on 2009-03-09
> **cdenley said:**
> You need to change your proxy settings. I'm not sure how to do that in Xubuntu, but you're definitely trying to use an incorrect proxy.

You were right, I just looked and for some reason I had anon-proxy installed, I uninstalled and restarted and it all is fine. Interesting. Thanks for your time I really appreciate it.

---

