---
title: "scripting questions"
date: 2011-02-26
forum: Gaming &amp; Leisure
---

### Post by wog on 2011-02-26
I'm thinking about setting up a minecraft server. I found instructions about setting up a server here:
[http://ubuntuforums.org/showthread.php?t=1667154](http://ubuntuforums.org/showthread.php?t=1667154)

But I don't know scripting. 

Is $USER a place marker for whatever my username is, or should I actually type in $USER where it says to type it?

---

### Post by down_to_earth_sort_of_guy on 2011-02-26
<pre>
down_to_earth_sort_of_guy@server:~$ echo $USER
down_to_earth_sort_of_guy
</pre>

so leave $USER as $USER it will translate to whatever your current user is.

---

### Post by keltic dave on 2011-02-27
> **wog said:**
> I'm thinking about setting up a minecraft server. I found instructions about setting up a server here:
[http://ubuntuforums.org/showthread.php?t=1667154](http://ubuntuforums.org/showthread.php?t=1667154)

But I don't know scripting. 

Is $USER a place marker for whatever my username is, or should I actually type in $USER where it says to type it?

[http://bukkit.org/](http://bukkit.org/) 

a much better server client than the default one notch provides.

---

### Post by wog on 2011-02-27
> **keltic dave said:**
> [http://bukkit.org/](http://bukkit.org/) 

a much better server client than the default one notch provides.

Um, that would be great, but I don't see a way of downloading it, so it's kind of useless until then. Especially for someone like me who doesn't code or know how to script.

---

### Post by keltic dave on 2011-02-27
you shouldn't need script at all though 

Bukkit
[http://ci.bukkit.org/job/dev-Bukkit/418/artifact/target/bukkit-0.0.1-SNAPSHOT.jar](http://ci.bukkit.org/job/dev-Bukkit/418/artifact/target/bukkit-0.0.1-SNAPSHOT.jar)

Craftbukkit
[http://ci.bukkit.org/job/dev-CraftBukkit/457/artifact/target/craftbukkit-0.0.1-SNAPSHOT.jar](http://ci.bukkit.org/job/dev-CraftBukkit/457/artifact/target/craftbukkit-0.0.1-SNAPSHOT.jar)

download both create a folder call it whatever you want.

then inside the folder put the 2 files inside. 

create a new empty file name it launcher.sh or startup.sh open it up and copy this into it.

```
java -Xms512M -Xmx1024M -jar craftbukkit-0.0.1-SNAPSHOT.jar
```save the file right click it properties go to the permissions tab make it executable. 

Double click on it select the Run in terminal

Thats it you have a server.

Then if you go the bukkit forums there is a section for all kinds of cool plug-ins to mess around with.

*Note if you edit the xms and xmx thats the ram that will be dedicated to it so you can increase those.*

---

### Post by wog on 2011-02-27
Okay, that's 'way cool! I was even able to connect to it, unlike the other install. Bukkit and craftbukkit are cool! :)

---

### Post by keltic dave on 2011-02-27
No problem it's basically the same method with the standard server only with bukkit you can add plugins to make the server experience a much richer one. 

Like the really cool plugin called levelcraft which adds a sort of RPG level system to it.

---

### Post by wog on 2011-02-27
Um, question, though. 

In server.properties is an entry for server.ip which is blank.
Does my external ip go there? Or my internal ip (inside the router)?

---

### Post by keltic dave on 2011-02-27
shouldn't need to touch that all you need to do is make sure your router and ubuntu forward 25565. Then anyone that wants to connect just give them your external ip with the port 25565 at the end.

---

### Post by wog on 2011-02-27
I'm getting a weird behavior from playing now.

I dig out a block and then the block reappears, and if I wait long enough, the block finally vanishes again.

Unfortunately, by the time all this takes place, the sun has marched most of the way across the sky.

Is there a way to solve this, or is this just one more of the current bugs?

---

### Post by keltic dave on 2011-02-27
Could possibly be not sure of the current build of minecraft mp haven't played it in a few weeks.

---

### Post by wog on 2011-02-27
Minecraft Beta 1.3_01

...this is what you meant by 'minecraft mp', right?

---

### Post by alegomaster on 2011-02-27
Actually the beta server software is 1.3. The game is 1.3_01

---

### Post by donkyhotay on 2011-02-27
> **wog said:**
> I'm getting a weird behavior from playing now.

I dig out a block and then the block reappears, and if I wait long enough, the block finally vanishes again.

Unfortunately, by the time all this takes place, the sun has marched most of the way across the sky.

Is there a way to solve this, or is this just one more of the current bugs?

That's because of lag, the client reports you cleared the block so it vanishes, the server reports there should be a block there so it reappears, then the server updates with the lost block and it vanishes again. It's something I see often on multiplayer servers. Nothing you can do about it that I know of.

---

### Post by wog on 2011-02-28
The new minecraft_server.jar update fixed my problems. I can now connect with my vanilla server.

The interesting thing I note about this version is, aside from the console window they give you now, is that the lag behavior is gone for at least 15 minutes before it starts showing up, along with the server message about maybe being overloaded.

I guess a dual-core 3 GHz machine with 3 Gigs of ram isn't enough for it, even playing on the laptop. I remember reading someone else had a machine dedicated to the game with 8 Gigs of ram. Maybe it's time to build a new machine!

---

