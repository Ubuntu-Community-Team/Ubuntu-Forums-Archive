---
title: "Remote desktop viewer help"
date: 2009-06-09
forum: General Help
---

### Post by letmekilluplz on 2009-06-09
1 - I want to be able to log in to my desktop from my laptop and download stuff onto my desktop and add it to Transmission. Can remote desktop viewer do that ? 

2 - What is the effective range is it just on the same network or anywhere with internet access? 

3 - When I try to log in I get a error of ```
Connection to host sean@sean:5900 was closed.
```

Sorry for the barrage of questions but I didn't want to spam with multiple posts.

---

### Post by StooJ on 2009-06-10
If it is just for Transmission, you can do it by switching on the Transmission Web Interface. Have a look at the Web tab in the Transmission Settings. Then you can access & control Transmission via a web browser.

This'll work locally, and if you want to expose it to the world you could open the appropriate port on your router & forward the traffic to the right PC. Best to set up a username & very good password if you're going to do this though.

If you're wanting remote desktop for other things too, then Remote Desktop can do that, yes. I would advise you do it over SSH however.

---

### Post by letmekilluplz on 2009-06-10
I only want it for transmission but I do need to be able to access it from other  places so how would I go about forwarding traffic to my laptop.

I know how to port forward although it never seems to work :(

---

### Post by nothingspecial on 2009-06-10
You could use [ssh]("http://principialabs.com/beginning-ssh-on-ubuntu/")

On your desktop ```
sudo apt-get install openssh-server
```

On your laptop

 ```
ssh -X username@ipaddress
```

```
wget torrent_file_you_want_to_download
```


Open transmission and away you go.

I would recommend using rtorrent in conjunction with [[COLOR="Cyan"]screen[/COLOR]]("http://www.manpagez.com/man/1/screen/") though. See [[COLOR="Red"]here[/COLOR]]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/") for instructions.

---

### Post by StooJ on 2009-06-10
> **nothingspecial said:**
> 
I would recommend using rtorrent in conjunction with [[COLOR="Cyan"]screen[/COLOR]]("http://www.manpagez.com/man/1/screen/") though. See [[COLOR="Red"]here[/COLOR]]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/") for instructions.

Why run the risk of a full-blown SSH server if it is unnecessary? Wouldn't the simple web interface that Transmission provides be a simpler, more "sandboxed" solution?

---

### Post by letmekilluplz on 2009-06-10
> **nothingspecial said:**
> On your desktop ```
sudo apt-get install openssh-server
```

On your laptop

 ```
ssh -X username@ipaddress
```

```
wget torrent_file_you_want_to_download
```


Open transmission and away you go.

I would recommend using rtorrent in conjunction with [[COLOR="Cyan"]screen[/COLOR]]("http://www.manpagez.com/man/1/screen/") though. See [[COLOR="Red"]here[/COLOR]]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/") for instructions.

That will work but I'm lost at the wget part. Can I download the torrent on my laptop and use transmission to download the actual "file" or does the file already have to be on my laptop? 

I'm not getting a visual display is this all command line?

---

### Post by nothingspecial on 2009-06-10
> **StooJ said:**
> Why run the risk of a full-blown SSH server if it is unnecessary? Wouldn't the simple web interface that Transmission provides be a simpler, more "sandboxed" solution?

You have a good point although learning about ssh is no bad thing. I started my own ssh adventure wanting to accomplish exactly the same thing.

What I should have done is explain what ssh is. To that end I`ve edited my post to include a link to a beginners tutorial on ssh.

---

### Post by letmekilluplz on 2009-06-10
That was a great tutorial and really helped a lot, but I didn't see any way to connect from other than the same network. 


I'm going on vacation and I want to be able to download files at home while I'm gone any ideas?

---

### Post by StooJ on 2009-06-10
> **nothingspecial said:**
> You have a good point although learning about ssh is no bad thing. I started my own ssh adventure wanting to accomplish exactly the same thing.

What I should have done is explain what ssh is. To that end I`ve edited my post to include a link to a beginners tutorial on ssh.

Awesome. SSH is ridiculously useful.

> **letmekilluplz said:**
> That was a great tutorial and really helped a lot, but I didn't see any way to connect from other than the same network. 

I'm going on vacation and I want to be able to download files at home while I'm gone any ideas?

You can SSH from another network, but you'll probably need to set up port-forwarding on your router. SSH uses port 22 by default, but you can always change that to something less obvious.

Unfortunately, the procedure for port-forwarding will depend on your model of router. You may find your model, along with instructions on how to forward ports at [http://portforward.com/](http://portforward.com/)

---

### Post by nothingspecial on 2009-06-11
> **StooJ said:**
> Awesome. SSH is ridiculously useful.



You can SSH from another network, but you'll probably need to set up port-forwarding on your router. SSH uses port 22 by default, but you can always change that to something less obvious.

Unfortunately, the procedure for port-forwarding will depend on your model of router. You may find your model, along with instructions on how to forward ports at [http://portforward.com/](http://portforward.com/)

Changing the port is essential for security. To access your pc from the outside world see [here]("http://aaobloggers.wordpress.com/2009/02/25/sshopenssh-guide/") You also need to have a static ip address for your router. See [[COLOR="Red"]here[/COLOR]]("http://www.dyndns.com/") and [[COLOR="Lime"]here[/COLOR]]("https://help.ubuntu.com/community/DynamicDNS")

Make sure you understand the security implications before setting this up. I recommend using keys rather than a password and disabling root login. You`ll see what I mean after you`ve read those pages.

---

### Post by letmekilluplz on 2009-06-12
Ok so after a some thinking I managed to get my ssh working :D 

I have:

- Set up a dynamic DNS
- Inserted a public key
- Changed the default port
- Port forwarded
- Inserted a MaxAuthTries 
- Changed the config so I only have to type ssh sean instead of domain, user, etc.

If there is anything I have missed to make it more secure, usable, or that may mess it up please post and let me know.

And a few questions

- How can I edit the config file so I don't have to type ssh sean -XC to forward X?
- Is there a way to test and see if I can connect from a different network without connecting to a different one?

Thanks so much

---

### Post by nothingspecial on 2009-06-12
> **letmekilluplz said:**
> 

If there is anything I have missed to make it more secure, usable, or that may mess it up please post and let me know.




Use encryption

```
ssh -X -C -c blowfish
```

See [COLOR="Red"][here]("http://en.wikipedia.org/wiki/Blowfish_(cipher)")[/COLOR]

---

