---
title: "Installing a file..."
date: 2009-03-11
forum: General Help
---

### Post by Shiv4m on 2009-03-11
Hello I'm finally back on this forum to ask questions :)

I want to know how can I install this "sun-java6-jdk"

Please give me noob instructions, thank you...

---

### Post by Shiv4m on 2009-03-11
Hello I'm finally back on this forum to ask questions :)

I want to know how can I install this "sun-java6-jdk"

Please give me noob instructions, thank you...

---

### Post by Therion on 2009-03-11
System/Administration/Synaptic Package Manager
Search Box:  sun-java6-jdk
Click to install, allow dependencies, and apply changes.

---

### Post by anlag on 2009-03-11
Doing it the GUI way:

1. Go to System -> Administration -> Synaptic Package Manager, enter password.

2. In Synaptic, go to Settings -> Repositories.

3. Under the Ubuntu Software tab, ensure the multiverse line is checked. Close the Repository window.

4. If you just had to enable multiverse, hit Reload in Synaptic.

5. In Synaptic, search for the name of the package, in your case sun-java6-jdk.

6. When the package shows up in the list, right-click it and select "mark for installation."

7. Apply.



If you already have multiverse enabled, entering this in a terminal would suffice:

> sudo apt-get install sun-java6-jdk

---

### Post by overdrank on 2009-03-11
Threads merged :)

---

