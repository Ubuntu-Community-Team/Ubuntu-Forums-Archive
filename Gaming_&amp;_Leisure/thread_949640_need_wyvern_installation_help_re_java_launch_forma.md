---
title: "need wyvern installation help re: java launch format"
date: 2008-10-16
forum: Gaming &amp; Leisure
---

### Post by strider22 on 2008-10-16
I have installed wyvern in /usr/games/wyvern and the launch script returns an error. Can you give me suggestions. This appears to be a java question more than a game question.

I downloaded the linux install.jar file from [http://www.cabochon.com/wyvern/download#notes](http://www.cabochon.com/wyvern/download#notes)
installed sun-java-5 using the synaptic installer.
ran "java -jar install.jar" into /usr/games/wyvern

The instructions are;
To run the Wyvern Client, create a launcher for your system that contains the following command. (Assumes you've installed it in the directory: /wyvern/client)
```
java -Dwyvern.home="/wyvern/client/wyvern" \
-cp "wyvernclient.jar;jl020.jar;jogg-0.0.5.jar;jorbis-0.0.12.jar;mp3sp.1.5.jar;vorbisspi0.7.jar" \
wyvern.client.Client
```

I removed the \s and created a single command line and adjusted for my install directory;
```
java -Dwyvern.home="/usr/games/wyvern" -cp "wyvernclient.jar;jl020.jar;jogg-0.0.5.jar;jorbis-0.0.12.jar;mp3sp.1.5.jar;vorbisspi0.7.jar" wyvern.client.Client

```

Run from the command line I get;
```

chris@beryllium:/usr/games/wyvern$ java -Dwyvern.home="/usr/games/wyvern" -cp "wyvernclient.jar;jl020.jar;jogg-0.0.5.jar;jorbis-0.0.12.jar;mp3sp.1.5.jar;vorbisspi0.7.jar" wyvern.client.Client
Exception in thread "main" java.lang.NoClassDefFoundError: wyvern/client/Client

```

run in a script I get;
Unable to access jarfile wyvern.client.Client

I am guessing that wyvern.client.Client at the end is the class to run although the / slashes in the returned error message above look a lot like directory slashes and the message says jarfile??
I have thrashed variations of the class at the end because I don't know if wyvern.client.Client is an internal class hierarchy or if the wyvern.client part is the file directory. It never works.

Java -help shows;
```

-cp <class search path of directories and zip/jar files>
-classpath <class search path of directories and zip/jar files>
            A : separated list of directories, JAR archives,
            and ZIP archives to search for class files.
```
so I changed the ; into : but still no difference

I also tried putting the class right after the -cp

Oh, yeah and I've made the directory and all files 777 for now.

Thanks for any assistance.

---

