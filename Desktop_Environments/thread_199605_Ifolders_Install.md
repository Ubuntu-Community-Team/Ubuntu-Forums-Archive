---
title: "Ifolders Install"
date: 2006-06-19
forum: Desktop Environments
---

### Post by mat_london on 2006-06-19
Hi,

I've followed the Howto here :

[http://www.ifolder.com/index.php/HowTo:Building_iFolder_Enterprise_Server_on_Dapper](http://www.ifolder.com/index.php/HowTo:Building_iFolder_Enterprise_Server_on_Dapper)

And it has worked so far.
But when I try and run simiasserver I get this :

Error: The Simias server has not been configured.
Please run simias-server-setup in order to configure the
Simias server.

However simias-server-setup does not exist on my system.

Also when I run 

simias-user create --user "jripper" --password "1234" --first "Jack" --last "Ripper" --full "Jack The Ripper" --email "jripper@domain.com" --url "http://localhost"

I get 

Failed creating jripper's account.

Anyone had this too ?
Anyone know the answer ?

I've installed the ifolder3-server-3.5.6167.1 version.
I'm getting the login screen OK at both [http://ubuntu/admin/](http://ubuntu/admin/) & [http://ubuntu/ifolder](http://ubuntu/ifolder)

Mat

---

### Post by GameGod on 2006-06-20
I just ran into this problem too...

Here's what I did to get around it:
I went into the "ifolder-server-3.5.6171.1/src/server/setup" folder and ran "make".
After that, I did:
sudo cp SimiasServerSetup.exe /usr/bin
sudo cp simias-server-setup /usr/bin

Then I ran "sudo simias-server-setup"

:)
Good luck!

---

### Post by mat_london on 2006-06-20
Great that now works, but what the hell did you enter under the simias-server-setup
process ?  :D 

Mat

---

### Post by jamisonaw on 2006-06-25
[QUOTE=mat_london] what the hell did you enter under the simias-server-setup
process ?[/QUOTE]

My question exactly. The wiki on Ifolder.com for Dapper skips this step completely. I have tried configuring it a few different ways, but keep getting this error:

> Configuring /etc/simias/Simias.config...SetupSimias - Done
Setting up permissions.../bin/chown: `wwwrun:www': invalid user
Failed

System.Exception: Unable to set an owner for the store path.
in <0x001c7> Novell.iFolder.SimiasServerSetup:SetupPermissions ()
in <0x00027> Novell.iFolder.SimiasServerSetup:Configure ()
in <0x00051> Novell.iFolder.SimiasServerSetup:Main (System.String[] args)
in <0x001c7> Novell.iFolder.SimiasServerSetup:SetupPermissions ()
in <0x00027> Novell.iFolder.SimiasServerSetup:Configure ()
in <0x00051> Novell.iFolder.SimiasServerSetup:Main (System.String[] args)

FAILED
](*,) 
Anyone have any suggestions? Must I configure a user first?

I really need to get iFolder up and running. I have a school full of teachers who need file sharing!

All help is appreciated.

---

### Post by mat_london on 2006-06-25
Thats exactly what I'm getting too.

I'm sure that this is what any Ubuntu user is going to get. 

Ubuntu Users ?


Mat

---

### Post by mat_london on 2006-06-27
Are there really only four of us on the planet trying to get this to work.
A look from anyone with Ifolders Server up and running would be apreciated.

Bump :-D 

Mat

---

### Post by Poldi on 2006-06-30
count me in. 

I got an older iFolder version running with SimpleServer on Hoary once (after days of fiddeling), but I had no luck yet on Dapper with either the workgroup or the Enterprise server version.

some months ago rumor had it that iFolder should appear in the regular Dapper repo in the near future - does anyone know who is working on this?

---

### Post by naked on 2006-06-30
Apparently we are the only ones who wants this... what I don't understand is why this isn't hugely popular.  It seems like the perfect solution for a LOT of problems.  I would actually consider paying for iFolder hosting... but not a lot!

L

---

### Post by crxyem on 2006-06-30
Add me to the list as well, I'm working on getting this installed on Kubuntu
iFolder seems like the best solution compared to win2k3 servers folder redirection. which I'm not particularly thrilled about the way it works.

I've got to this point

[QUOTE=mat_london]Great that now works, but what the hell did you enter under the simias-server-setup
process ?  :D 

Mat[/QUOTE]


I've got the setup running but no clue how to begin. 

Simias is looking for 

Server's data path []? 


which I have no clue as to what it might be.

I found some info that might help lead in the correct direction for running the setup. see refference for installing via cygwin on windows
[http://www.ifolder.com/index.php/HowTo:Building_iFolder_Enterprise_Server_on_Windows](http://www.ifolder.com/index.php/HowTo:Building_iFolder_Enterprise_Server_on_Windows)

   Host:          any
   Port:          any
   Virtual path:  /simias10/
   Physical path: c:\iFolderServer\web
Listening on port: 8086
Listening on address: 0.0.0.0
Root directory: c:\iFolderServer
Simias Application Path: c:\iFolderServer
Simias Data Path: c:\iFolderServer\simias
Run in server configuration
Local service port = 8086
Files found in exising simias data area... Ignoring bootstrap process
Simias Process Starting
Simias Process Running
[http://127.0.0.1:8086/simias10](http://127.0.0.1:8086/simias10)
c:\iFolderServer\simias

Novell's documentation says that the data path is were the application and user directories get created.

---

### Post by naked on 2006-06-30
I'm not sure if it matters.  I've gone through the setup a few times, at the end you will get the above error and you will have to create a user and a group to get it to finish the setup.  But even them you cannot run simiasserver, it says the setup hasn't been run yet.

The setup creates a config file which can be edited at a later date I believe, so I think our problem lies elsewhere.

L

---

### Post by crxyem on 2006-06-30
> Configuring /etc/simias/Simias.config...SetupSimias - Done
Setting up permissions.../bin/chown: `wwwrun:www': invalid user
Failed


Look at the setting permissions error, I created a user www-run and a group www and ran the simias-server-setup. and all is well 

I can get a login prompt via [http://localhost/admin](http://localhost/admin)  /simias10

but I can't seem to create a user


I'm pretty sure the iFolder server is running, I get a login screen and enter admin info, but immediately says my session has timed out.

---

### Post by valorin on 2006-07-04
I have the same problem...

I'll go digging around in the config files tomorrow, see if I can manually get it to do something.

---

### Post by naked on 2006-07-04
[QUOTE=crxyem]Look at the setting permissions error, I created a user www-run and a group www and ran the simias-server-setup. and all is well 

I can get a login prompt via [http://localhost/admin](http://localhost/admin)  /simias10

but I can't seem to create a user


I'm pretty sure the iFolder server is running, I get a login screen and enter admin info, but immediately says my session has timed out.[/QUOTE]

Have you tried to connect from another box with the iFolder client?

L

---

### Post by valorin on 2006-07-07
With regards to the issue with simias-server-install complaining about permissions, here is the solution I used:

I created a file: /etc/apache2/uid.conf which reads:
```
User wwwrun
Group www
```

*(Ok, thats by memory, so I could be wrong...)*

However, although it got me through my the installer, it still didn't solve my problem.

---

### Post by valorin on 2006-07-07
Ok, I finally got it to work!!

I followed the instructions, ignoring the "sudo simiasserver" lines. Once it had finished installing I restarted my server, and then went to [http://my.server/admin/](http://my.server/admin/) and logged in with:
user: admin
pass: simias

It let me straight in. From there I could add user accounts, and do other such stuff.
Don't bother with the command-line account addition method, do it through the web-interface. It worked for me.

I was also able to log into iFolder from the client easily.

Thats about all I can say on the matter.. I did nothing special, it just worked...

---

### Post by msbose on 2006-07-12
I tried the install by skipping "sudo simiasserver".  I tried admin/simias to login and it fails :(

---

### Post by cidco on 2006-07-13
When i run simasserver i get an error saying "Error: The Simias server has not been configured.
Please run simias-server-setup in order to configure the
Simias server." Even though i have gone through simias-server-setup. Is anyone else experiencing this?

---

### Post by valorin on 2006-07-14
msbose, The only advice I can give is restart your machine. I did that, then visited [http://localhost/admin/](http://localhost/admin/) and loged in with admin/simias

cidco, Thats the problem everyone has been having. I ignored it, restarted my machine and then was able to login... I can't explain why it worked.

---

### Post by msbose on 2006-07-15
Unfortunately I had already tried rebooting and still no success.  I may have installed a different package than you?](*,)

---

### Post by valorin on 2006-07-15
Hrm... I used the most recent package linked to by the howto, so I don't know.

---

### Post by mat_london on 2006-07-16
OK,

Could anyone who has got Ifolders Server to install and run take a few minutes to talk those of us who are still trying through how you managed it.

Sources, instructions etc

Thanks

Mat

---

### Post by valorin on 2006-07-16
I'll try and outline as much as I can... But yeah...

I went through the howto [here]("http://www.ifolder.com/index.php/HowTo:Building_iFolder_Enterprise_Server_on_Dapper")
Notes:
 - My system was a fresh install, using the LAMP-Server option
 - I **built libflaim** myself, I didn't use the repo
 - I manually edited the *configure.in* file, changing the mentioned line and commented out the others
 - I then used *sudo make install*

I then moved onto the howto [here]("http://www.ifolder.com/index.php/HowTo:Configure_iFolder_Enterprise_Server_on_Dapper")
Notes:
 - In addition to the missing directory listed there, I also created (and set permissions) to */var/lib/simias*
 - I ignored the error messages generated with these commands:
```
sudo simiasserver
sudo simiasserver --stop
```
 - I removed the directories listed:
```
rm -rf /tmp/.wapi
rm -rf /tmp/apache-temp-aspnet-0
rm -rf /var/lib/simias/*
```
 - I think I also ran these commands, but I can't remember exactly.
```
sudo mkdir -p /var/www/.config/.mono/
sudo chown -R www-data.www-data /var/www/.config/
```
 - I did **not** bother with the *create users* instructions
 
I then restarted my machine, and was able to login fine, using an external machine. From there I created a new user, and got everything else to work.

I'm not at home, so, thats as much detail as I can remember from what I did. I have an idea as to something else which might be a factor, but I need to confirm it when I get home.

Hope this helps...

---

### Post by [Yatta] on 2006-07-17
I did the same thing valorin did. I DID do 
> sudo mkdir -p /var/www/.config/.mono/
sudo chown -R www-data.www-data /var/www/.config/

because when i did try to login I i got a time out error.

My problem now is that I'm trying to upload another file (a pdf to be exact) but it not going through. :-/
 I'm able to send some files but not others? The file in question is 43mb... but earlier i was able to do upload a 23mb file.

Another thing i want to try and fix is the simias-server-setup. i don't want to create the **wwwrun:www **user/group like Valorin did. I think we should be able to manually edit some file where we can specify what apache  group/user we want to use. I want to change from **wwwrun** to **www-data**

---

### Post by valorin on 2006-07-17
That file-size issue could be an upload limit in Apache itself, rather then an issue with iFolder.

Also, with the simias-server-setup user issue, when I was struggling to get iFolder working I used this method to stop the error:

I created a file: /etc/apache2/uid.conf which reads:
```
User wwwrun
Group www
```

Basically the installer looks for that file, to tell it the user and group names. If the file doesnt exist then it uses its own defaults.
I have no idea if this will solve your problem, but it worked for me when I tried it (in one of my many trials to get iFolder working) I haven't bothered to use it on my current install, as I got it working.

---

### Post by [Yatta] on 2006-07-17
the ***/etc/apache2/uid.conf*** worked just fine.. I'll have to look into that file size thing though. thanks

---

### Post by valorin on 2006-07-17
Cool, good to know it solved your problem :)

---

### Post by cidco on 2006-07-18
ok im getting closer but for some reason, my web url is different than most, I have to access from [http://host/simias10](http://host/simias10) from there i get a login prompt, but i just get a 404 error when i try [http://host/admin](http://host/admin) . any ideas?

---

### Post by Sq322 on 2006-07-18
I would love to use this program. It is exactly what i need and just the way i need it, but it seems WAY to labor intensive at this point to install

---

### Post by valorin on 2006-07-19
cidco, Not a clue. Sorry :( Check your apache stuff?

Sq322, Yeah, it takes time to setup, but once its working its amazing simple! You often don't need to touch it and it does it job!

---

### Post by joneZ on 2006-07-19
> **valorin said:**
> cidco, Not a clue. Sorry :( Check your apache stuff?

Sq322, Yeah, it takes time to setup, but once its working its amazing simple! You often don't need to touch it and it does it job!


Setup the Ifolder Server is not the problem ( after some days of trying and trying and trying  ;-) ), had some more problems to compile it under x86_64.,

but I can't use the Client ?? 

I tried version 3.5 and 3.4 Windows and Linux, I get always the same 
error in the Simias.log :-(

```

2006-07-19 13:16:23,257 [1132812640] DEBUG Simias.Sync.Log - Released Lock count = 0
2006-07-19 13:16:23,262 [1132812640] DEBUG Simias.Sync.Log - Acquired Lock count = 1
2006-07-19 13:16:23,263 [1132812640] DEBUG Simias.Sync.SyncService - BeginListAllNodes start
2006-07-19 13:16:23,263 [1132812640] DEBUG Simias.Sync.SyncService - BeginListAllNodes End
2006-07-19 13:16:23,264 [1132812640] DEBUG Simias.Sync.Log - Request Failed exception
Argument cannot be null.
in <0x0064c> System.String:FormatHelper (System.Text.StringBuilder result, IFormatProvider provider, System.String format, System.Object[] args)
in <0x0004d> System.String:Format (IFormatProvider provider, System.String format, System.Object[] args)
in <0x0001d> System.String:Format (System.String format, System.Object[] args)
in <0x0015b> Simias.SimiasAccessLogger:LogAccess (System.String method, System.String uri, System.String id, System.String status)
in <0x00276> Simias.Sync.SyncService:BeginListAllNodes ()
in <0x00407> Simias.Sync.SyncService:Start (Simias.Sync.StartSyncInfo si, System.String user, System.String sessionID)
in <0x00142> Simias.Sync.Http.HttpService:StartSync (System.Web.HttpRequest request, System.Web.HttpResponse response, System.Web.SessionState.HttpSessionState session)
in <0x00232> Simias.Sync.Web.SyncHandler:ProcessRequest (System.Web.HttpContext context)


```

Does it work for you  ?


Upload in Webinterface is not the problem ...


Hell I don't know why only a few people are interested in ifolder.

For me it is the perfect solutions for everything of my problems !!

Greetings
Erik

---

### Post by joneZ on 2006-07-19
> **Sq322 said:**
> I would love to use this program. It is exactly what i need and just the way i need it, but it seems WAY to labor intensive at this point to install

what is you problem ??

Maybe I can help you, write me Mail to evetters gmail com


Erik

---

### Post by valorin on 2006-07-19
> **joneZ said:**
> but I can't use the Client ?? 
I tried version 3.5 and 3.4 Windows and Linux, I get always the same 
error in the Simias.log :-(

Hrm.. Have you tried the Troubleshooting from the wiki page?
[https://help.ubuntu.com/community/iFolderClient](https://help.ubuntu.com/community/iFolderClient)

Wait.. Windows error as well?

Are you using a port on your address in the accounts dialog? I know SimpleServer used a port, but the enterprise server doesn't use one.

---

### Post by cptnapalm on 2006-07-19
cidco:  I get a warning from apache on start saying that the Alias directive in /etc/simias/apache/default/simias_server.conf on line 3 will probably never match.  That is the line which tells apache about simias10.  I *think* that what is going on on my system is that there are two competing apache config files for the same thing.

Novell didn't make this easy for us non RPM people...

Edit:  Ok... I've noticed that there are three Simias.conf files installed and two Simias.Server.conf files.  Not even getting into the mess it is making of my filesystem (why do I have a /usr/web and a /etc/simias/bill... bill?)  It has, as far as I can tell, conflicting apache config files.

While I can get to a login, the provided default simply does not work.  The ifolder.com HOWTO is deficient; things happen which it does not take note of.

I need an icon of me slamming someone else's head into a brick wall...

---

### Post by joneZ on 2006-07-20
Hi, 

Yes Novell makes it really hard, for non SLES User's.  But maybe
it takes time or they have no resources. 


> **naked said:**
> I'm not sure if it matters.  I've gone through the setup a few times, at the end you will get the above error and you will have to create a user and a group to get it to finish the setup.  But even them you cannot run simiasserver, it says the setup hasn't been run yet.

The setup creates a config file which can be edited at a later date I believe, so I think our problem lies elsewhere.

L

I did the following to get the  stuff working ..

```

./autogen --prefix=/usr --sysconfdir=/etc
make
make install

```


and then I created the following dirs 

```

mkdir /var/www/.config
mkdir /var/www/.config/.mono

mkdir /var/lib/simias

chown -R www-data:www-data /var/www/.config
chown -R /var/lib/simias

```


And the the apache config, in my /etc/apache2/sites-available/default
I but the following. I do not have any other yet. It lookes like this
under everything else.

```

#ifolder

Alias /admin "/usr/lib/simias/admin"
Alias /ifolder "/usr/lib/simias/webaccess"
Alias /simias10 "/usr/lib/simias/web"

AddMonoApplications admin "/admin:/usr/lib/simias/admin"
AddMonoApplications ifolder "/ifolder:/usr/lib/simias/webaccess"
AddMonoApplications simias10 "/simias10:/usr/lib/simias/web"

<Location /simias10 >
    MonoSetServerAlias simias10
    Order allow,deny
    Allow from all
    #AddHandler mono asax aspx ascx asmx ashx log csv
    SetHandler mono
</Location>

<Location /admin >
    MonoSetServerAlias admin
    Order allow,deny
    Allow from all
    AddHandler mono asax aspx ascx asmx ashx log csv
    DirectoryIndex Default.aspx index.html
</Location>


<Location /ifolder >
    MonoSetServerAlias ifolder
    Order allow,deny
    Allow from all
    AddHandler mono asax aspx ascx asmx ashx
    DirectoryIndex Default.aspx index.html
</Location>


</VirtualHost>

```


The I did ...

```

a2enmod mono 

```

My mod_mod.conf is the default from Ubuntu default installation


The I put the simias Config in /var/lib/simias, it looks like this

```

Simias.config in /var/lib/simias
Simias.log4net in /var/lib/simias

mkdir /var/lib/simias/modules
Simias.server.conf in /var/lib/simias/modules

```

Attached you will find the Simias.config and Simias.log4net

Under /etc/simias I have the same files / directory structure but 
I one file more defaults.config


```

<configuration>
  <section name="DefaultServerValues">
    <setting name="simiasdatadir" value="/var/lib/simias" />
    <setting name="runasclient" value="FALSE" />
  </section>
</configuration>

```


And last but not least I did 

```


/etc/init.d/apache2 start


```


And it lookes like this 

```

www-data  4224  0.0  0.4  59388  4116 ?        S    12:56   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4230  0.0  0.4  59388  4116 ?        S    12:56   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4232  0.0  1.0  36988 11084 ?        Ssl  12:56   0:00 /usr/lib/pkgconfig/../../bin/mono /usr/lib/xsp/1.0/mod-mono-server.exe --filename /tmp/.mod_mono_server --nonstop --appconfigdir /etc/mono-server
www-data  4248  0.0  0.9  36052 10208 ?        Ssl  12:56   0:00 /usr/lib/pkgconfig/../../bin/mono /usr/lib/pkgconfig/../../lib/xsp/1.0/mod-mono-server.exe --filename /tmp/mod_mono_server_admin --applications /admin:/usr/lib/simias/admin --nonstop
www-data  4314  0.0  0.4  59388  4116 ?        S    12:56   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4323  0.0  0.4  59388  4116 ?        S    12:56   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4368  0.0  0.4  59388  4116 ?        S    12:56   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4372  0.0  0.9  36052 10188 ?        Ssl  12:56   0:00 /usr/lib/pkgconfig/../../bin/mono /usr/lib/pkgconfig/../../lib/xsp/1.0/mod-mono-server.exe --filename /tmp/mod_mono_server_ifolder --applications /ifolder:/usr/lib/simias/webaccess --nonstop
www-data  4373  0.0  0.4  59388  4116 ?        S    12:56   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4379  0.0  0.4  59388  4116 ?        S    12:56   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4383  0.0  0.4  59388  4116 ?        S    12:56   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4424  0.0  0.9  36052 10188 ?        Ssl  12:56   0:00 /usr/lib/pkgconfig/../../bin/mono /usr/lib/pkgconfig/../../lib/xsp/1.0/mod-mono-server.exe --filename /tmp/mod_mono_server_simias10 --applications /simias10:/usr/lib/simias/web --nonstop
www-data  4438  0.0  0.4  59388  4116 ?        S    12:56   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4442  0.0  0.4  59388  4116 ?        S    12:56   0:00 /usr/sbin/apache2 -k start -DSSL
root      4860  0.0  0.0   3980   916 pts/0    R+   13:13   0:00 grep www-data


```

And now I can go to 

[http://localhost/admin](http://localhost/admin) and 
[http://localhost/ifolder](http://localhost/ifolder) 


and works like a charme


But sill can't acces with a client ... maybe my fault.


Greetings
Erik

---

### Post by joneZ on 2006-07-20
> **valorin said:**
> Hrm.. Have you tried the Troubleshooting from the wiki page?
[https://help.ubuntu.com/community/iFolderClient](https://help.ubuntu.com/community/iFolderClient)

Wait.. Windows error as well?

Are you using a port on your address in the accounts dialog? I know SimpleServer used a port, but the enterprise server doesn't use one.


- No ports default 8036 and changed it to 80

I can see the following in Simias.log when I want to sync from a client.
He looks in fine. and the when he want to sync. 

```

2006-07-19 14:12:14,291 [1080584544] DEBUG Simias.Storage.ChangeLog - Added ChangeLogWriter for collection 169334aa-0166-4e81-b190-946b446ff3702006-07-19 14:12:14,297 [1128544608] DEBUG Simias.Storage.Journal - Updating journal in tester
2006-07-19 14:12:14,300 [1128544608] DEBUG Simias.Storage.Journal -     record = 8257:0f6b2e61-8e43-4211-95ea-2f654ae36166:786eaecb-e196-4164-9726-5294185ac987:632889151342284320:Erik Vetters
2006-07-19 14:12:14,326 [1092663648] DEBUG Simias.Server.Catalog - ignoring event fired from the catalog collection
2006-07-19 14:12:14,326 [1134913888] INFO  Simias.Server.Catalog - Collection: 169334aa-0166-4e81-b190-946b446ff370 created
2006-07-19 14:12:14,326 [1090562400] DEBUG Simias.Server.Catalog - ignoring event fired from the catalog collection
2006-07-19 14:12:14,355 [1128544608] DEBUG Simias.Storage.Journal - Updating journal in tester
2006-07-19 14:12:14,360 [1128544608] DEBUG Simias.Storage.Journal -     record = 33:0f6b2e61-8e43-4211-95ea-2f654ae36166:50af7306-f7b2-4f46-91a1-02cefccc911b:632889151342284320:tester
2006-07-19 14:12:14,362 [1092663648] DEBUG Simias.Server.Catalog - ignoring event fired from the catalog collection
2006-07-19 14:12:14,362 [1134913888] DEBUG Simias.Server.Catalog - Member 0f6b2e61-8e43-4211-95ea-2f654ae36166 added to collection 169334aa-0166-4e81-b190-946b446ff370
2006-07-19 14:12:14,362 [1090562400] DEBUG Simias.Server.Catalog - ignoring event fired from the catalog collection
2006-07-19 14:12:14,372 [1134913888] DEBUG Simias.Server.Catalog -
2006-07-19 14:12:14,372 [1134913888] DEBUG Simias.Server.Catalog - Catalog Entry
2006-07-19 14:12:14,372 [1134913888] DEBUG Simias.Server.Catalog -      Erik's Testordner
2006-07-19 14:12:14,373 [1134913888] DEBUG Simias.Server.Catalog -      CID: 6ea23427-74a6-4ce1-a6ef-cefb8ca4be16
2006-07-19 14:12:14,373 [1134913888] DEBUG Simias.Server.Catalog -      HID: 066db6d6-db2c-4086-a230-8539202566ce
2006-07-19 14:12:14,373 [1134913888] DEBUG Simias.Server.Catalog -      Members
2006-07-19 14:12:14,373 [1134913888] DEBUG Simias.Server.Catalog -              0f6b2e61-8e43-4211-95ea-2f654ae36166
2006-07-19 14:12:14,373 [1134913888] DEBUG Simias.Server.Catalog -
2006-07-19 14:12:14,373 [1134913888] DEBUG Simias.Server.Catalog -
2006-07-19 14:12:14,373 [1134913888] DEBUG Simias.Server.Catalog - Catalog Entry
2006-07-19 14:12:14,373 [1134913888] DEBUG Simias.Server.Catalog -      tester
2006-07-19 14:12:14,374 [1134913888] DEBUG Simias.Server.Catalog -      CID: 169334aa-0166-4e81-b190-946b446ff370
2006-07-19 14:12:14,374 [1134913888] DEBUG Simias.Server.Catalog -      HID: 066db6d6-db2c-4086-a230-8539202566ce
2006-07-19 14:12:14,374 [1134913888] DEBUG Simias.Server.Catalog -      Members
2006-07-19 14:12:14,374 [1134913888] DEBUG Simias.Server.Catalog -              0f6b2e61-8e43-4211-95ea-2f654ae36166
2006-07-19 14:12:14,374 [1134913888] DEBUG Simias.Server.Catalog -
2006-07-19 14:12:17,112 [1139640672] DEBUG Simias.Sync.Log - Released Lock count = 1
2006-07-19 14:12:17,115 [1139640672] DEBUG Simias.Sync.Log - Acquired Lock count = 2
2006-07-19 14:12:17,116 [1139640672] DEBUG Simias.Sync.Log - Request Failed exception
Argument cannot be null.
in <0x0064c> System.String:FormatHelper (System.Text.StringBuilder result, IFormatProvider provider, System.String format, System.Object[] args)
in <0x0004d> System.String:Format (IFormatProvider provider, System.String format, System.Object[] args)
in <0x0001d> System.String:Format (System.String format, System.Object[] args)
in <0x0015b> Simias.SimiasAccessLogger:LogAccess (System.String method, System.String uri, System.String id, System.String status)
in <0x002fd> Simias.Sync.SyncService:BeginListChangedNodes (System.Boolean contextValid)
in <0x0036e> Simias.Sync.SyncService:Start (Simias.Sync.StartSyncInfo si, System.String user, System.String sessionID)
in <0x00142> Simias.Sync.Http.HttpService:StartSync (System.Web.HttpRequest request, System.Web.HttpResponse response, System.Web.SessionState.HttpSessionState session)
in <0x00232> Simias.Sync.Web.SyncHandler:ProcessRequest (System.Web.HttpContext context)


```


but wait maybe I have to use diffrent ports ?? Will try that out


Greetings
Erik

---

### Post by saracen on 2006-07-27
I just read this from the FAQ on the iFolder website:

> Using iFolder to share without the server allows you to synchronize and share files between two or more computers without the requirement for an intermediate server to exchange files. This is accomplished through add-on modules being developed in the open-source community. There are two methods under development to allow users to share using Gaim, the open-source instant messaging client, and using Bonjour (Rendevous).

So does this mean I can just install the client on Linux and then have someone else install the client on Windows and we can both share files with each other?  If not then what is the status of the add-on modules that it mentions and how do they integrate with the iFolder client?

---

### Post by flloyd on 2006-07-27
[http://www.ifolder.com/index.php/FAQ#I_can.27t_seem_to_figure_out_how_to_share_in_workgroup_mode.2C_why_not.3F](http://www.ifolder.com/index.php/FAQ#I_can.27t_seem_to_figure_out_how_to_share_in_workgroup_mode.2C_why_not.3F)

---

### Post by vanstrien on 2006-09-14
I'm giving this threat a little bump in the hopes that someone who got this working is around.

I _did_ have this working, but in trying to recreate my steps and put together some fresh packages I lost it.  I was able to login to /admin and /ifolder, and both windows and linux clients could sync via /simias10.  This was all through apache versus simpleserver.  Sometimes a new directory/share wouldn't sync though, which is why I didn't just leave it be.  In restrospect...

My biggest problem is that I get a 404 error on /simias10 now, even though I am sure it is configured.  

Any one have any suggestions?

---

### Post by BastNic on 2006-09-19
Hi, 

I need some information about ifolder entreprise server used with multidomain. I have well done the two steps "Install" and "configure". Now I tryed to follow [this]("http://www.ifolder.com/index.php/HowTo:Configure_MultiDomain_iFolder_Enterprise_Server").

Problem: It's don't work. I tried with two local ips and juste one (the first) works. I note when I modify something in /var/lib/toto/simias/Simias.config, the server don't care. Do you know if mono or simias have a cache or something else ?

And I'm sorry for my english, mais je suis français et je fais ce que je peux (I'm Frensh and i try to do the best i can)

---

