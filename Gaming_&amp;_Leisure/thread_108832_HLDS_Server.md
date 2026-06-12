---
title: "HLDS Server"
date: 2005-12-27
forum: Gaming &amp; Leisure
---

### Post by Gooks on 2005-12-27
I will show you how to make a Half-Life Dedicated Server.


Linux

Steam and Cs1.6 Install Guide

    Install Guide:


          Intro:

          This Guide is written for help with installing the new steam linux 1.6 server.
          It will take you step by step through the installation until you have a basic Counter-Strike server running.


          Requirements:

             1. Acces to Linux server with ssh, or your own server with a keybord.
             2. An Internet connection on the linux server.
             3. An homedir where you have write acces.
             4. Enough space on your hard drive, 600Mb At least.
             5. wget or an ftp program.
             6. Gzip unpack program. 


          Guide:

          Ok, Lets get started.
          Go to your homedir and lets make a new dir for the server, and then go into that dir.
          Should you already have a installation you want to update, just use the hlds_l dir you using now

               mkdir hlds_l

          Now lets go in the dir.

               cd hlds_l

          Now we are going to download the steam install files (file is called steam) I use wget here to get the file.
          If you are having problems downloading this file from this location there are some mirrors listed at the bottom of this page.
          if your linux doesnt have wget, use the http/ftp program provided with your distribution to get it.

               wget [http://users.lichtsnel.nl/~jap/steam/steam.tar.gz](http://users.lichtsnel.nl/~jap/steam/steam.tar.gz)

          We now have the file we need, now lets unpack it!

               tar -zxvf steam.tar.gz

          Now make sure it executable.

               chmod +x steam

          now lets runs steam:

               ./steam

          it will response with:

               Checking bootstrapper version ...
               Getting version X of Steam HLDS Update Tool
               Downloading. . . . . . . . . . .
               Steam Linux Client updated, please retry the command

          Now we are all ready to start getting an acount for steam, and to get the files!
          The thing we are going to do is create an account for our dedicated server, ill give the correct syntax plus an example:

               ./steam -command create -username <username> -email <email> -password <password> -question <question> -answer <answer>

               ./steam -command create -username Japje -email [email]jap@valvesoftware.com[/email] -password hard2guess -question "does steam r0x?" -answer yes

          Now you know how it must be done, so lets do it, go make an account.

          After creating the account steam will response with:

               Checking bootstrapper version ...
               Creating Account
               Account Created successfully

          So we now have an updated steam client, and an account for this server, cool huh now lets get those server files.

               ./steam -command update -game <game> -dir /path/to/your/hlds_l -username <username> -password <password> -remember_password

          As you can see we can choose our game, install dir, with our username and password we just created,
          and putting -remember_password at the end will make sure it remembers the password.
          The install dir is the path to the hlds_l dir we made in the beginning, ill use /home/jap/hlds_l as an example.

               ./steam -command update -game cstrike -dir /home/jap/hlds_l -username Japje -password hard2guess -remember_password

          if you typed it correctly it will response with:

               No installation record found at /home/jap/hlds_l
               Checking/Installing 'Counter-Strike Base Content' version XX

          It will now start downloading files, go and watch tv, come chat in the irc channel, it will take some time.
          Dont worry about the no installation record found error, its just an message that it didnt found any installion, since its the first time


          If steam is done downloading all those files, you will be back at the prompt, and you basicly now have an ready to use cs server
          you can test the server if it works with:

               ./hlds_run -game cstrike +map de_dust -autoupdate

          This wil run the most basic cs server with the map de_dust.
          The option -autoupdate will make sure that if there is a Counter-Strike game update that it wil download it Automaticly

          Because we made steam remember our password, all we need to do to update next time is run:

               ./steam -command update -game <game>

          Thats all, How to config the server, thats all up to you, that im hoping, i dont need to explain.
          I wish you best of luck with your new Dedicated Linux Counter-Strike Server!
          I would like to thank the whole valve team for 2 things, this linux version, and the use of their Readme file while creating this guide!

          Also if you have any questions or you just want to chat, join us on irc:
          for server problems/questions:
          #counter-server on Gamesurge
          or for chatting:
          #steam-hangout on Gamesurge

          Mirrors for steam.tar.gz

          [http://users.lichtsnel.nl/~jap/steam/steam.tar.gz](http://users.lichtsnel.nl/~jap/steam/steam.tar.gz)
          [http://68.90.68.35/steam.tar.gz](http://68.90.68.35/steam.tar.gz)
          [http://japje.nl/steam/steam.tar.gz](http://japje.nl/steam/steam.tar.gz)
          [http://tehshith0le.net/japje/steam.tar.gz](http://tehshith0le.net/japje/steam.tar.gz)


          Powered by [www.Travel-info.nl](www.Travel-info.nl) 

Credits to [http://japje.nl/steam/install](http://japje.nl/steam/install)

---

### Post by hav0x on 2005-12-27
Man ... they'd have to **PAY ME** quite the amount of money to host one 'o those.

Steam ... *shivers*

---

### Post by bjweeks on 2005-12-28
This how-to is outdated.

---

