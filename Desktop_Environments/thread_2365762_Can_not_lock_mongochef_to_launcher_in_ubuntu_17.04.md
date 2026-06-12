---
title: "Can not lock mongochef to launcher in ubuntu 17.04"
date: 2017-07-10
forum: Desktop Environments
---

### Post by caneraydinbey on 2017-07-10
I downloaded mongochef.

Then i go to its bin folder and run this

&#10140;  ~ cd Program\ Files/studio-3t-5.3.5-linux-x64/bin  
&#10140;  bin ./studio-3t.sh  

Then on launcher , i click add to dash + lock the launcher.

Then i exit mongochef. 

I still see icon on launcher.

I click it to launch, it is pending. It is like it will start , it is getting bigger smaller it is just like it will start but it wont start.

This is desktop entry in
.local/share/applications

name is program.desktop
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=Studio 3T for MongoDB - TRIAL LICENSE
Icon=program
Path=/home/caner/Program Files/studio-3t-5.3.5-linux-x64
Exec=/home/caner/Program Files/studio-3t-5.3.5-linux-x64/bin/../jre/bin/java -Dprism.order=sw -jar /home/caner/Program Files/studio-3t-5.3.5-linux-x64/bin/../lib/data-man-mongodb-ent-5.3.5.jar
StartupNotify=false
StartupWMClass=Studio 3T
OnlyShowIn=Unity;
X-BAMFGenerated=true
```

this is studio_3t.desktop
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=Studio 3T for MongoDB - TRIAL LICENSE
Icon=program
Path=/home/caner/Program Files/studio-3t-5.3.5-linux-x64/bin
Exec=/home/caner/Program Files/studio-3t-5.3.5-linux-x64/bin/../jre/bin/java -Dprism.order=sw -jar /home/caner/Program Files/studio-3t-5.3.5-linux-x64/bin/../lib/data-man-mongodb-ent-5.3.5.jar
StartupNotify=false
StartupWMClass=Studio 3T
OnlyShowIn=Unity;
X-BAMFGenerated=true

```

---

### Post by ajgreeny on 2017-07-10
In the pathway shown there is a space which needs escaping or the full pathway enclosing in quotes.

Try editing the desktop file and escaping the space where it says **/Program Files/** by using **/Program\ Files/** in all instances where it appears in the desktop file.

---

### Post by caneraydinbey on 2017-07-10
But in same folder, there is intellji and it works

```
[Desktop Entry]
Version=1.0
Type=Application
Name=IntelliJ IDEA
Icon=/home/caner/Program Files/idea-IU-171.4694.70/bin/idea.png
Exec="/home/caner/Program Files/idea-IU-171.4694.70/bin/idea.sh" %f
Comment=The Drive to Develop
Categories=Development;IDE;
Terminal=false
StartupWMClass=jetbrains-idea
```

---

### Post by caneraydinbey on 2017-07-10
But it worked :D tyhan k you

i changed the fodler name to ProgramF&#305;les

---

### Post by deadflowr on 2017-07-10
> But in same folder, there is intellji and it works
The Exec line is wrapped in quotes.

Something to ponder, does it show your proper icon for the intellij launcher?
(I doubt it)
As there is no such image called Program, most likely.
(Which is what the Icon line would read, since it stops at Program un-escaped and unwrapped in quotes)

Edit: moot point now if you renamed the folder...

---

### Post by ajgreeny on 2017-07-10
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

