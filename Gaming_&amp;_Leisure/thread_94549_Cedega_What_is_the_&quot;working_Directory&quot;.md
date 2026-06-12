---
title: "Cedega: What is the &quot;working Directory&quot; ?"
date: 2005-11-24
forum: Gaming &amp; Leisure
---

### Post by Biased turkey on 2005-11-24
I tried to install Panzer general III with cedega 5.0
The installation added the title in the leftmost column of cedega, then added an icon to the right column.
The game couldn't be played so i deleted it and reinstalled with the windows 2000 option. But then the icon disapeared.
When right clicking on the title in the leftmost column in order to reinstall the icon I'm asking to specify the path for the executable and the working directory.
I know what the 1st path is, it's the path to the .exe file
What's the path to the **working directory** ? what does it means ?
tia for any advise or info.

---

### Post by claydoh on 2005-11-24
[cedega should automatically do this for you]("http://downloads.transgaming.com/files/Cedega-How-To-5.0.0-2.html#6.1.2.Advanced%20Installation%20Options%7Coutline") so it probably is not needed.

the working directory is the dir the application's exe is located. Some windows apps need this to be specified, ( iirc C:\program Files\mygame, but I am not sure of this, the linux type path my work). Some apps cannot be called from another directory, i.e running the command from ~/<myhomedir>, they need to be called from the dir the executable is in.

---

