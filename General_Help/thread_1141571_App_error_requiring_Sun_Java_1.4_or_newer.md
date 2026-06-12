---
title: "App error requiring Sun Java 1.4 or newer"
date: 2009-04-28
forum: General Help
---

### Post by the_nite_owl on 2009-04-28
Hi All.
This worked normally for a long time and started giving me an error about 4-5 months back.

I run an Aventail client to connect through my companies firewall to remote desktop.  When I manually run startctui.sh script to start Aventail it tells me "Aventail Connect needs Sun Java 1.4 or newer; your Java appears unsuitable."

I can tell it to run anyway and it does run fine but it is a nuisance.  I would like to run it from an icon on my desktop as I used to.  Now I have to manually run it.

I am not sure what it is looking for for Java.  I am running Sun Java 6 Runtime.  I believe this is the same version I was running back when this worked without error messages.

Anyone have an idea?

---

### Post by the_nite_owl on 2009-04-28
Never mind, I found the solution.
I had Java 6 installed but I also had OpenJDK installed and I guess it was picking up on that one and Aventail was not recognizing it as a supported version.  
Once I uninstalled OpenJDK it began working again.

Now if I can figure out how to not let Aventail lock up my IP connection.
It used to be I could have the remote desktop session running and still access the internet in my Ubuntu desktop.  Now as long as Aventail Connect is open I cannot connect to web sites through Ubuntu, only through the remote desktop session.

---

