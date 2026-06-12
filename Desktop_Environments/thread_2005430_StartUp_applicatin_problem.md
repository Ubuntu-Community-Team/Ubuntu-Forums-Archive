---
title: "StartUp applicatin problem"
date: 2012-06-17
forum: Desktop Environments
---

### Post by mmistroni on 2012-06-17
Hi all
 i am trying to startup two applications i have on my Ubuntu laptop at startup time
I went to startup application and entered these two commands:

/usr/lib/jvm/java-6-oracle/bin/java -jar "/home/marco/javadev/SpringInteg-1.0-SNAPSHOT/SpringInteg-1.0-SNAPSHOT.jar" 

/usr/lib/jvm/java-6-oracle/bin/java -jar "/home/marco/javadev/Camel-App/camel-app-1.0-SNAPSHOT.jar"


The problem i have is that, when i add the SpringInteg application, and then the CAmelApp, somehow the CamelApp 'overrides' the SpringInteg, and instead of having 2 startup application i have only one.

If i add a startup  for CamelApp first, and then SpringInteg, the SpringInteg will override the CAmelApp

I cannot undestand why this is happening. is it because i am starting up both application with same command?

w/kindest regards
 marco

---

### Post by MG&amp;TL on 2012-06-17
Can you post a screenshot of your startup applications dialog?

It's a little confusing as to what you are doing, and more information helps us give better advice.

---

### Post by mmistroni on 2012-06-17
Hello
  i have problems in getting screenshots here. :(
here's what i do
1 - StartUp Application
2 - Add
3 - Enter a name (Camel App)
4 - Enter the command
    /usr/lib/jvm/java-6-oracle/bin/java -jar "/home/marco/javadev/Camel-App/camel-app-1.0-SNAPSHOT.jar"
5  - Enter a description 
6 - Click on 'Add'

I then repeat the same process for the other applicatin (SpringInteg... .jar), and click 'Add'
Both applications shows up in the StartUp Application list of applications starting up

i then close the StartUp application screen.

the next time i re-open the StartUp application Preferences screen, i only see the startup application i have entered last (SpringInteg)

I managed to get around it by adding one of the two app to the /etc/init.d scripts, but  i am curious on why i cannot add more than one StartUp application....

anyone could assit?

w/kindest regards
 marco

---

### Post by MG&amp;TL on 2012-06-17
> **mmistroni said:**
> 
I managed to get around it by adding one of the two app to the /etc/init.d scripts, but  i am curious on why i cannot add more than one StartUp application....

anyone could assit?

w/kindest regards
 marco

No, you couldn't. X hasn't started when init.d starts. I'm assuming these are graphical apps.

Anyway, a possible solution would be to add a third "buffer" start app, which does nothing. Set the command to "echo hello" or something.

---

### Post by mmistroni on 2012-06-18
Hello
 no they are not graphical app./ they are two standalone java app , one based on camel and the other based on SpringInteg

will carry on investigating..

for the moment, the camelapp start with init.d (i have created a script) while the springinteg is added to startup app

w./kindest regards
 marco

---

