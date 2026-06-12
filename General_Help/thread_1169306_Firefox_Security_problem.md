---
title: "Firefox Security problem"
date: 2009-05-25
forum: General Help
---

### Post by rofflesupplecake on 2009-05-25
I have been running into a problem with Firefox recently, whenever I open firefox I get the following message:
"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

And I cannot visit any SSL encrypted sites like paying for amazon or using my email and I get this following error:
"Secure Connection Failed

          

[www.google.com]("http://www.google.com") uses an invalid security certificate.

The certificate is not trusted because the issuer certificate is unknown.

(Error code: sec_error_unknown_issue)


    * This could be a problem with the server's configuration, or it could be someone trying to impersonate the server.

    * If you have connected to this server successfully in the past, the error may be temporary, and you can try again later."


Is there anyway this can be fixed?

---

### Post by Oblivion_4 on 2009-05-25
ok so whats happening is that firefox does have the rights to access the what ever the file it uses to initialize security because the operating system is denying it the right to do so.

To fix the problem run firefox in terminal and try to sign into a website like amazon again. When you receive the error message again pull up the terminal that you are using to run firefox and look through the lines of text until you find a phrase like "**permission denied**" for a certain file in a certain directory.

To fix the problem you need to change the permissions of the file that firefox needs by running "chmod 777 thefilename" in terminal in the directory where the file resides.

also if you need to sign in before you get back and can't because firefox isn't implementing ssh you can sign in by running firefox in terminal with "sudo firefox"

---

### Post by rofflesupplecake on 2009-05-25
> **Oblivion_4 said:**
> ok so whats happening is that firefox does have the rights to access the what ever the file it uses to initialize security because the operating system is denying it the right to do so.

To fix the problem run firefox in terminal and try to sign into a website like amazon again. When you receive the error message again pull up the terminal that you are using to run firefox and look through the lines of text until you find a phrase like "**permission denied**" for a certain file in a certain directory.

To fix the problem you need to change the permissions of the file that firefox needs by running "chmod 777 thefilename" in terminal in the directory where the file resides.

Sorry :(, but I really do not know how to follow all of these steps as I just started using ubuntu since a few weeks now. How do you open FF in the terminal or change permissions for the file?

---

### Post by Oblivion_4 on 2009-05-25
to open up a terminal, click applications in the top right, then go to accessories, then click terminal

to run firefox in terminal, simply type firefox in the terminal and hit enter

now whenever you run an application in a terminal it display all of the output you need to see. Oh yeah don't close the terminal when you run firefox or firefox will close too. whenever you do anything in firefox such as open a new tab text will appear in the terminal.

To find what file firefox can't access, you need to replicate the error so that the terminal will display test about the error. The error should say something like "permission denied" without the quotes.

Once you find the permission denied error copy and paste the text from the terminal and all of the text around it so we can help you solve your problem 

kthxbye

---

### Post by rofflesupplecake on 2009-05-25
The terminal isnt showing me the output in the screen :(. Your method isnt working, but thanks anyways.

---

