---
title: "Parsing Arguments Problem"
date: 2011-01-21
forum: Education &amp; Science
---

### Post by abqorian on 2011-01-21
Hi all, this is my first thread in this forum. But I have been watching this site for long time though.

I'll be direct. My code was perfectly fine, but I wanted to run several robots. So I need to pass the port number, ./program -p 6670, am I correct?

Then, I have a problem while parsing that argument in Player/Stage (P/S). I have three argument -h <host>, -p <port>, -b <battery>
The program only parse the third argument, batt.
This is the code: firstfile.cpp
```


#include <unistd.h>
#include <libplayerc++/playerc++.h>
#include <iostream>

//some global variables

using namespace std;
using namespace PlayerCc;

string		gHostname(PlayerCc::PLAYER_HOSTNAME);
uint32_t	port(PlayerCc::PLAYER_PORTNUM);
uint32_t	gIndex(0);

PlayerClient		robot(gHostname, port);
Position2dProxy		pp(&robot,gIndex);
SonarProxy		ir(&robot,gIndex);

//some functions that take either pp, ir, and/or robot declared above, for example

void wWalk() {
	pp.SetSpeed(SPEED, 0);
}
void doRole(char c){
	switch(c){
		case 'w': worker(); break;
		case 'f': forager(); break;
		case 's': bystander(); break;
	}
}
char checkRole(float battery){
	if(battery > BATTERY_HALF){ 
		cout <<"Robot is a worker"<<endl;
		return 'w';}
	if(battery > BATTERY_THIRD){
		cout <<"Robot is a forager"<<endl;
		return 'f';}
	else {
		cout <<"Robot is in standby"<<endl;
		return 's';}
}
void print_usage(int argc, char** argv) // print program usage to user
{
	//using namespace std;
	cerr << "USAGE:  " << *argv << " [options]" << endl << endl;
	cerr << "Where [options] can be:" << endl;
	cerr << "  -h <hostname>  : hostname to connect to (default: "
		<< PlayerCc::PLAYER_HOSTNAME << ")" << endl;
	cerr << "  -p <port>      : port where Player will listen (default: "
	<< PlayerCc::PLAYER_PORTNUM << ")" << endl;
	cerr << "  -b <battery>   : battery level at start (default: random)"
	<< endl;
}

int parse_args(int argc, char** argv){
	batt = initiateBattery();
	//const char* optflags = "h:p:b:";
	int ch;
	
	while(-1 != (ch = getopt(argc, argv, "h:p:b:")))
	{
		switch(ch)
		{
		// case values must match long_options
			case 'h': // hostname
				gHostname = optarg;
				break;
			case 'p': // port
				port = atol(optarg);
				break;
			case 'b': // battery
				batt = atoi(optarg);
				break;
			case '?':
			case ':':
			default:  // unknown
				print_usage(argc, argv);
				exit (-1);
		}
	}
	return 0;
}

int main(int argc, char** argv) {

	parse_args(argc,argv);

	robot.Read();
	cout << "Robot: "<<robot<<" is a walking."<<endl;
	cout << "Host is: "<<gHostname<<" on port: "<<port<<endl;
	while(batt>0){
		char role = checkRole(batt);
		doRole(role);
	}
	return 0;
}

```

After trying to solve it, I found out the cause (maybe). 
It was because I initiated PlayerClient before the calling parsing_argument function. So, maybe Player already put 'hostname' and 'port' even before receiving values from parse_args().

The problem is I need to put
```

PlayerClient		robot(gHostname, port);
Position2dProxy		pp(&robot,gIndex);
SonarProxy		ir(&robot,gIndex);

```

before main() so that I could type wWalk() instead of ```
wWalk(Position2dProxy &pp)
```
But then when I type ./firstfile -p 6666 -b 56
the program seem to take -b input only, P/S still run robot on port 6665.

So, I tried to kinda rearrange the code: secondfile.cpp
```

//the same line
PlayerClient*		robot;
Position2dProxy*	pp;
SonarProxy*		ir;
//some functions
void wWalk(Position2dProxy &pp) {
	pp.SetSpeed(SPEED, 0);
}
void doRole(char c, PlayerClient &robot, Position2dProxy &pp, SonarProxy &ir){
	switch(c){
		case 'w': worker(robot, pp, ir); break;
		case 'f': forager(robot, pp, ir); break;
		case 's': bystander(robot, pp, ir); break;
		//default : worker();break;
	}
}
//the same line
int main(int argc, char** argv) {
	
	parse_args(argc,argv);
	string		gHostname(PlayerCc::PLAYER_HOSTNAME);
	uint32_t	port(PlayerCc::PLAYER_PORTNUM);
	uint32_t	gIndex(0);
	robot		= new PlayerClient(gHostname, port);
	pp			= new Position2dProxy(robot,gIndex);
	ir			= new SonarProxy(robot,gIndex);

	robot->Read();
	cout << "Robot: "<<robot<<" is a worker"<<endl<<
	"Hostname: "<<gHostname<<" with port "<<port<<endl;

	while(batt>0){
		char role = checkRole(batt);
		doRole(role, robot, pp, ir);
	}

	return 0;
}

```

but when I 'make' the file. it returned error something like:
```

error:invalid initialization of reference of type 'PlayerCc::PlayerClient&' from expression of type 'PlayerCc::PlayerClient*'

error: in passing argument 2 of 'void doRole(char, PlayerCc::PlayerClient&, PlayerCc::Position2dProxy&, PlayerCc::SonarProxy&)'

```

What is happening here? 
How to correctly call PlayerClient as global (atop the main()), to avoid writing function like ```
worker(PlayerClient &robot, Position2dProxy &pp, SonarProxy &ir)
```
Please, any help is appreciated. I've been searching forums around internet for almost three days now looking for the solution.
I'm not giving up, but I feel this is the time to ask :D

Thanks in advance,
Abe

---

