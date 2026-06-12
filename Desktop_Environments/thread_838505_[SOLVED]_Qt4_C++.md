---
title: "[SOLVED] Qt4 C++"
date: 2008-06-23
forum: Desktop Environments
---

### Post by tornado89 on 2008-06-23
I' Creating A Server-Client Simulation On Ubuntu Hardy Using
C++....
I Chose QT4 As GUI.. 
At First I Created A pushButton, textEdit & a listWidget
And Then Connected The Signal ( clicked() ) from the button
to a Function That Sends The "textEdit" Contents To The Server
And Copy The Contents Also To The listWidget...& Till Now All Went OK
And The Widget Text Got Updated...
But when the Client Receives A Message From The Server I Try To 
Update The listWidget.. But Nothing Happens... 
The Function Responsible To Update The listWidget is 

void Output( char* Msg ); And It's Called From Within The Receive() 
Function of The Server

I Made Sure That The Function Is Called When The Server Is Called But
The Statement 

listWidget->addItem( Msg ); Doesn't Update The Widget Text !!!

Do I Have To Connect The Function Receive In Anyway To The listWidget ??!!

---

### Post by tornado89 on 2008-06-24
Thanks.. I managed To Solve The Problem And Decided To post
It For Future Reference If Needed

The Problem Is Because QT4 Doesn't Support fork() 
I Had To Create A Thread Class Using Sub-Class QThread
And Then emit a custom SIGNAL from Within The Class
And SLOT it To A Function From Within The Program main exec Thread

---

