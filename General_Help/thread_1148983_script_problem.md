---
title: "script problem"
date: 2009-05-04
forum: General Help
---

### Post by ajhtiredwolf on 2009-05-04
ok so I have this script 
cd /home/wolf/.wine/drive_c/Program\ Files/Star\ Wars\ Jedi\ Knight\ Jedi\ Academy/GameData/ && env WINEPREFIX="/home/wolf/.wine" wine "C:\Program Files\Star Wars Jedi Knight Jedi Academy\GameData\jamp.exe"

the name of the script is jamp. Im using it with gfire which is a program within pidgin that can launch the game a friend is on. So the problem is, if I add to the end of the script for instance jamp.exe" +connect 192.168.0.2 
then that will connect to the server just fine. However if I try and do this jamp +connect 192.168.0.2 it will not work. I need it to work like this because gfire is passing the arguments +connect ip:port ( where ip is the ip that it gets and port is the port it gets from pidgin) and it will add that argument to the end of the script. So my idea was to have the script do this \GameData\jamp.exe" nameofsomefile
and have nameofsomefile contain +connect 192.168.0.2 and have gfire write the ip:port to this file. How can I do this? how can I make the script read information as txt from a file at the end, and how can i have gfire  write this txt to that file. Here is what the inside of the gfire xml document looks like 


<?xml version='1.0' encoding='UTF-8' ?>

<launchinfo>
	<game id='4158' name='Jedi Academy Multiplayer' type='Native game'>
		<xqf name=''/>
		<processes unix_process='' windows_process=''/>
		<command>
			<bin>jamp</bin>
			<dir>/usr/local/bin</dir>
			<gamemod></gamemod>
			<connect> "+connect @ip@:@port@" > mytxt.txt</connect>
			<launch>@options@ @gamemod@ @connect@</launch>
		</command>
	</game>
</launchinfo>

---

