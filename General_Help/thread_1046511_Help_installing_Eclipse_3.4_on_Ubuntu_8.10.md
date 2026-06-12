---
title: "Help installing Eclipse 3.4 on Ubuntu 8.10"
date: 2009-01-21
forum: General Help
---

### Post by raveash on 2009-01-21
I'm trying to install Eclipse 3.4 on Ubuntu 8.10.I downloaded the latest version and have extracted it to my desktop. I renamed the extracted folder eclipse3.4. 

I have no problem running the program.My question is,what do i do now? I'm sure as hell not gonna leave this folder on my desktop!

I was thinking i could move the folder to "/usr/lib" but i'm not sure.

So, can anyone tell me where i can move this new eclipse3.4 folder?

Also, could some one also tell me how to make a shortcut??
I know how to make launchers, would that work??

Thanks! [-o<

---

### Post by sandyd on 2009-01-21
you could have installled eclipse from the resipostries, but since you asked...

First, copy the eclipse folder to whereever you want. Remember the location and make sure its writable by you. (for example, a good place would be "/opt""
Create a new file in 
~/bin

(~/ refers to your home directory)
called "eclipse"

with the path to the eclipse executable.

For example, if you coppied eclipse to /opt/eclipse
you would probably put 

```

/bin/sh -c /opt/eclipse/eclipse

``` 
inside the file you created in ~/bin  (assuming that the file name of the executable is "eclipse"

Then, assuming you got everything correct, typing "eclipse" in the terminal would launch eclipse

If you want the really easy way,
```

sudo apt-get install eclipse

```
should do it for you

---

### Post by raveash on 2009-01-23
The Eclipse 3.4 is not available in the 8.10 reposotories..only Eclipse 3.2 if I'm correct.....I want the latest version 3.4, so i have to install it manually....but thanks anyways...

---

### Post by Silvestro Fantacci on 2009-02-02
> **raveash said:**
> The Eclipse 3.4 is not available in the 8.10 reposotories..only Eclipse 3.2 if I'm correct.....I want the latest version 3.4, so i have to install it manually....

I have installed Eclipse 3.2 through the Synaptic Package Manager and the result is a launcher in "*Application* -> *Programming* -> *Eclipse*", which points to a (178 lines long!) "*/usr/bin/eclipse*" script, which in turn ends up running the "*/usr/lib/eclipse/eclipse*" application.

As I am also thinking of installing Eclipse 3.4.1, I wonder whether it would be a good idea to just remove 3.2 from "*/usr/lib/eclipse*" and place 3.4.1 there?

---

### Post by volchara on 2009-02-02
I unpack my Eclipse archives into /opt, rename the top-level eclipse directory according to the version (e.g. eclipse-3.4), then make a symlink /opt/eclipse -> /opt/eclipse-3.4, and then symlink ~/bin/eclipse to /opt/eclipse/bin/eclipse (or whatever the executable is).

---

### Post by gcastell on 2009-10-26
> **Silvestro Fantacci said:**
> I have installed Eclipse 3.2 through the Synaptic Package Manager and the result is a launcher in "*Application* -> *Programming* -> *Eclipse*", which points to a (178 lines long!) "*/usr/bin/eclipse*" script, which in turn ends up running the "*/usr/lib/eclipse/eclipse*" application.

As I am also thinking of installing Eclipse 3.4.1, I wonder whether it would be a good idea to just remove 3.2 from "*/usr/lib/eclipse*" and place 3.4.1 there?

I did this and it worked!

---

### Post by gcastell on 2009-10-26
> **gcastell said:**
> I did this and it worked!

Well, I wrote too soon! I had to follow two more steps:

1. Update the eclipse script under /usr/bin, remove all the parameters to run eclipse.
2. [http://aspyct.blogspot.com/2009/04/eclipse-cannot-connect-to-keystore.html](http://aspyct.blogspot.com/2009/04/eclipse-cannot-connect-to-keystore.html)

Good Luck!

---

