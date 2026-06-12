---
title: "Conky Script For All Hockey Fans"
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by RottenBananas on 2008-02-27
Hey guys,
Heres a script for conky I use to see how well my Philly Flyers are doing. Ive posted it up in various threads before but since the NHL changes the layout of the site I figure making a thread for it with fixes would be better. 

It shows the last games results,next game (updates score if the game is in progress), time and the channel itll be on.

I believe this is the final version...until the NHL changes the html again
All you have to do is change:

```
temp = urllib2.urlopen('http://flyers.nhl.com/index.html')
```

to:

```
temp = urllib2.urlopen('http://yourteamsnamehere.nhl.com/index.html')
```

and add this line to your .conkyrc

```
{execi 120 python /home/yourusername/whateveryoucalledthescript.py}
```

Im sure itll mess up in the future whenever the NHL changes the html so please post here if it does.

Heres the script

```
#written by Bananas
#change 'http://flyers.nhl.com/index.html to http://yourteamsname.nhl.com/index.html
#please post if you have any programming suggestions!
#i dont know python and really would like to learn so your tips are appreciated!

import urllib2
temp = urllib2.urlopen('http://flyers.nhl.com/index.html')
myFile = temp.read()

first = myFile.find('<div class="gameScoreboard">')
last = myFile.rfind("Recap")
section = myFile[first:last]

date = section.find("datetime alert")
if date == -1:
	date = section.find("datetime")

dateEnd = section.find("</div>")
if dateEnd == -1:
	dateEnd = section.find("&")
inProgress = 0
#game hasnt begun yet
nextGame = section[date+33:dateEnd-13]
if date == 77 and dateEnd == 138:
	nextGame = section[date+33:dateEnd-13]
	inProgress = 0

#game is in progress
#if date == 74 and dateEnd == 120 or date == 74 and dateEnd == 122 or date #== 74 and dateEnd == 121:
if date == 74 and dateEnd < 137:
	nextGame = section[date+21:dateEnd-4] + ' Period'
	inProgress = 1

if inProgress == 0:
	time = section.find('time',dateEnd)
	timeEnd = section.find('</div>',time)
	theTime = section[time+6:timeEnd]

if inProgress == 1:
	theTime = ''

team1 = section.find('teamName">')
team1end = section.find('</div>',team1)
awayTeam = section[team1+10:team1end]

team2 = section.rfind('teamName">')
team2end = section.find('</div>',team2)
homeTeam = section[team2+10:team2end]

awayScore = section.find('total">',team1)
awayScoreEnd = section.find('</div>',team1end+1)
totalAwayScore = section[awayScore+7:awayScoreEnd]

homeScore = section.find('total">',team2)
homeScoreEnd = section.find('</div>',team2end+1)
totalHomeScore = section[homeScore+7:homeScoreEnd]

channel = myFile.find('TV:&nbsp;')
channelEnd = myFile.find(',',channel)
theChannel = myFile[channel+9:channelEnd]

lastGame = section.find('page" title="')
if lastGame == -1:
	lastGame = section.find('<div class="teamName right">')
lastGameEnd = myFile.rfind('>Recap</a>')
if lastGameEnd == -1:
	lastGameEnd = section.find('<div class="teamName left">')

previous = section[lastGame+13:lastGameEnd]

if lastGame == 1722 and lastGameEnd == 1820 or lastGame == 1711 and lastGameEnd == 1809 or lastGame == 1709 and lastGameEnd == 1807:
	tempholder = section.find('</div>',lastGame)
	firstTeam = section[lastGame+28:tempholder]
	tempholder2 = section.find('</div>',lastGameEnd)
	secondTeam = section[lastGameEnd+27:tempholder2+2] 
	previous = firstTeam + ' @ ' + secondTeam

print 'Last Game:',previous[:-2]
print 'Next Game:',nextGame, theTime, theChannel
print ''
print 'Away Team:',awayTeam, totalAwayScore
print 'Home Team:',homeTeam, totalHomeScore
```


Attached is a screenshot of my desktop...you can see the script at the bottom of my conky.

Enjoy!

---

