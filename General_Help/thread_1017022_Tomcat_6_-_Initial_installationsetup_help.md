---
title: "Tomcat 6 - Initial installation/setup help"
date: 2008-12-20
forum: General Help
---

### Post by r1ch on 2008-12-20
Hi there,

I am trying to setup Tomcat 6 and am running into problems with setting up myself as an admin/manager user to access the manager webapp.

I have performed the following steps... can anyone offer some advice please?..

-Have used synaptic to install tomcat6, tomcat6-user, tomcat6-admin, tomcat6-examples

-Visiting [http://localhost:8080](http://localhost:8080) shows the "It works!" welcome page.

- I then altered the tomcat-users.xml file to input myself as an admin and manager in the following way...
  
  <role rolename="manager"/>
  <role rolename="admin"/>
  <user username="rich" password="12345" roles="manager,admin"/>

- on subsequently attempting to access the manager webapp and type in the user and password I am denied access.

I am at a bit of a loss as to how to proceed with this. Can anyone help please?

---

### Post by dude051 on 2008-12-20
This is because the default tomcat-users.xml files provided in the packages actually comment out the user info in the file. Be sure to erase the comment code before and after what you modified:

<!--
<role rolename="manager"/>
<role rolename="admin"/>
<user username="rich" password="12345" roles="manager,admin"/>
-->

Should just be:

<role rolename="manager"/>
<role rolename="admin"/>
<user username="rich" password="12345" roles="manager,admin"/>

I still wonder where and why they are commented in the debian tree... 

-Justin

---

### Post by r1ch on 2008-12-20
... and after removing the egg from my face and following your suggestion it works perfectly now.

I didn't even include the comment code in my original post so nice spot!

Thanks for your help

---

