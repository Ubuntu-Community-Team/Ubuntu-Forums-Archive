---
title: "program for message sequence diagram"
date: 2008-06-22
forum: Education &amp; Science
---

### Post by UbuGr on 2008-06-22
hello,
I search for a ubuntu program with can create message sequence charts like this

[IMG]http://www.cafesoft.com/products/cams/ps/docs20/program/CamsLoginModules/camsAuthenticationSequenceDiagram.gif[/IMG]

---

### Post by ProbablyX on 2008-06-26
There's a program called Umbrello (which is in the repos, comes via KDE)

There's also a proprietary program which is like Rational Rose, there's an evaluation license which I think is free to use for students and home users called Poseidon for UML ([http://www.gentleware.com/](http://www.gentleware.com/))

Hope it helps!

---

### Post by smhanov on 2008-07-05
Please have a look at [http://www.websequencediagrams.com](http://www.websequencediagrams.com). To get the above, you would just enter:

participant "Cams Authentication Service" as Service 
participant "JAAS LoginContext" as Context
participant "JAAS LoginModules" as Modules
participant "Session Object" as Object

Service->Context: create
Context->Modules: initialize
Service->Context: login
Context->Modules: commit
Service->Object: setLoginContext

---

