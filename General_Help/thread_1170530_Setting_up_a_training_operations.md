---
title: "Setting up a training operations"
date: 2009-05-26
forum: General Help
---

### Post by Pabs111 on 2009-05-26
[FONT=&quot]Hi[/FONT]
  
  [FONT=&quot]I am an Operations Manager for a small niche IT training company, and I would like to migrate our training operations to Ubuntu from Windows. I would like to have some understanding of how the following requirements can be implemented using Ubuntu. 
[/FONT]
[FONT=&quot]I’m a total newbie at Ubuntu and Linux, so please, any advice must be simple rather than a perfect.  [/FONT]
  
  [FONT=&quot]Background[/FONT]
  
  [FONT=&quot]1.[/FONT][FONT=&quot]We have around 50 IT development courses for which a laptop is provided to each student to perform development exercises during a course.[/FONT]
  [FONT=&quot]2.[/FONT][FONT=&quot]The laptops we use for our courses are of different technical specs. [/FONT]
  [FONT=&quot]3.[/FONT][FONT=&quot]Each student laptop, will have a base install of software (e.g. eclipse, tomcat, JAVA JDK etc) and then course specific software (with specific versions) installed on each laptop. [/FONT]
  [FONT=&quot]4.[/FONT][FONT=&quot]We cannot provide a server solution with laptops acting as dumb terminals due to networking issues.[/FONT]
  [FONT=&quot]5.[/FONT][FONT=&quot]Each time a laptop is used we provide a clean image of the laptop to ensure that any previous use of the laptop will not affect the current student.[/FONT]
  
  [FONT=&quot]Requirements[/FONT]
  [FONT=&quot]1.[/FONT][FONT=&quot]To be able to create a default environment of the base applications that can be “copied” to every laptop independent of the laptops technical spec. The default environment will be regularly updated as software applications are updated. The key point is that there is only one environment to copy to each laptop for any course and that we don’t need to apply updates on each laptop (outside of the OS)[/FONT]
  [FONT=&quot]2.[/FONT][FONT=&quot]To create a course specific environment that can be copied to each laptop that will be used during that course and will be “overlaid” on the default environment. The key point is the same as above, change once distribute to many. [/FONT]
  [FONT=&quot]3.[/FONT][FONT=&quot]For each new Student of the laptop, the laptop must be reverted to the standard environments. The student cannot change the underlying OS, i.e. no Student can affect the laptop for any subsequent use of that laptop. [/FONT]
  
  [FONT=&quot]Thanks for the help and just to restate that because of our lack of technical skills; a simple, even if time consuming solution, is preferable to a perfect solution which needs in depth technical knowledge. [/FONT]
  
  [FONT=&quot]Cheers[/FONT]
  
  [FONT=&quot]Paul [/FONT]

---

### Post by nebileix on 2009-05-26
> Requirements
1.To be able to create a default environment of the base applications that can be &#8220;copied&#8221; to every laptop independent of the laptops technical spec. The default environment will be regularly updated as software applications are updated. The key point is that there is only one environment to copy to each laptop for any course and that we don&#8217;t need to apply updates on each laptop (outside of the OS)[COLOR="Blue"]There's various way to install ubuntu with individual customizing of software. Check out these link. 
[http://ubuntu-tutorials.com/2007/10/14/automated-ubuntu-installation-preview/]("http://ubuntu-tutorials.com/2007/10/14/automated-ubuntu-installation-preview/")
[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/autodeploy]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/autodeploy")
Or you could just create a bash script to do the base software package installation that you need after the installation of ubuntu operation system. Install all software required for all courses so that you can use any laptops. You can disable the ability of access to those program based on permissions.
[/COLOR]
2.To create a course specific environment that can be copied to each laptop that will be used during that course and will be &#8220;overlaid&#8221; on the default environment. The key point is the same as above, change once distribute to many.[COLOR="Blue"]Create default user(s) based on courses name, specified any path variable and customization. Use group permission to filter the ability to run certain program depending on the courses that they are attending.[/COLOR]

3.For each new Student of the laptop, the laptop must be reverted to the standard environments. The student cannot change the underlying OS, i.e. no Student can affect the laptop for any subsequent use of that laptop. [COLOR="Blue"]Add new user and copy the home directory of the default user(s)(based on courses) into the new user directory and all settings will be default for each new student. Vice versa for removing of users.[/COLOR]

All of the above can be accomplished with the help of bash scripting. You will need certain knowledge in the operating system in order to automate stuff with bash. So for the time been, maybe spend more time doing it step by step, you'll need to play around with the permissions a lot. And it'll save your corporation lots of $$$.

Note: There might be certain bug with various hardware. Do make sure you check it out. Most of it have ways to work around it except for latest hardware which need more time as Linux is community driven.

Will be easier if your company could employ a Linux administrator to do all the job. If you intend to research and do it on your own, you might need month(s) to accomplish it.

Gd luck.

---

### Post by Pabs111 on 2009-05-31
Thanks [nebileix]("http://ubuntuforums.org/member.php?u=761332") for your advice. 

Looks like I need to get professional advice. 

Cheers

Paul

---

