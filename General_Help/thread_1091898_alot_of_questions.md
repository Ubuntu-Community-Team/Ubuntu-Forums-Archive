---
title: "alot of questions"
date: 2009-03-09
forum: General Help
---

### Post by hedoe on 2009-03-09
im planning to resurect an old Dell Deminsion 2400 from the grave of its 05 chains
Ubuntu is the freedom that it deserves
it has a good fast 2.8 Ghz unicore processor
but its being wayyy to stressed by trying to do everything on board
like graphics and audio
as well as the network and any other functions that windows has
so the plan:
a new PSU
a PCI vid card
a new 500 GB HDD
a higher CFM fan
hopefull OCing the CPU to 3 Ghz or 3.2
a fresh install of Ubuntu
then comes the fun part
i want to mount the cable modem
and the wireless g router inside the case
(im working on the plan for that)
so here are my questions:
1: is it possible to OC a cpu with ubuntu?
2: ive heard that ubuntu isnt very good at networks, would i have any problems or issues formatting my router?
3: how many GPUs could it support?
4: will i have any issues for any of my hardware that i all ready have? or want to get?
5: any thoughts or comments are welcome
thanks in advance for any help that can be provided

---

### Post by LegendofTom on 2009-03-09
I would be worried about some bottlenecking with that single core cpu.  You might be better off buying a new pc.

---

### Post by hedoe on 2009-03-09
im building a much better one
the only thing that i want to use this one for is to format my routers
i might look into making a slow SOHO server
and thats another reason why i want to OC the cpu

---

### Post by Rhubarb on 2009-03-09
What do you intend for this computer to be used for?
> the only thing that i want to use this one for is to format my routers
- This isn't very descriptive, if all you want to do is to configure your router, then for most routers all you have to do is to load up firefox on any computer on your LAN, and enter the IP address of your router (usually something like [http://192.168.0.1](http://192.168.0.1))

A SOHO server (filesharing, internet sharing) for 4 users isn't a demanding thing for a server to do.
Upgrading the video card in a server is rather foolish, as servers don't need to play 3D games in order to work well.
Also overclocking your CPU may indeed by useless, as I doubt the load on this server would be very high.

I would warn against mounting your cable modem inside the computer case, as I've found from experience that cable modems have a tendency to get very warm when operating, and if they happen to get too warm (due to lack of adequate ventilation), they crash and freeze up.

I would also strongly advise against putting a wireless g router inside your case as well, simply because computer cases are designed to sheild the computer from external radio interferance, and visa versa.
Putting a radio transmitter and receiver (wireless router) inside your case would be quite a foolish thing to do - In most wireless router manuals, you'll see that they advise you put their wireless routers atleast 2 meters away from any computing equipment.

The best thing that you can do to revive an old computer, is to give it lots more RAM (512MB minimum), give it a dust, perhaps a newer bigger hard drive, and put some Linux distribution on it (like Ubuntu / Ubuntu server).

You'd be surprised how little spec computer you can use as a home server running ubuntu server.
My home server is an 800MHz old laptop with a broken screen, 248MB RAM, 30GB HDD.
- It currently operates as a file server, a web server, a mumble (voip) server, and a games hosting server.  It's more than capable of running all of these, the only limiting factor really is my broadband internet connection.

---

### Post by hedoe on 2009-03-09
im afraid that i sadly left out some key parts
although you did bring up some good points
im going to make a custom bracket to hold the router and modem
which will also have fans that will keep it cool, i was thinking of getting some of the highest CFM fans for the size.
something like an 80mm can rated at 84.1 CFM having 2 of them side by side
over the router and modem
im also going to move the antennas to the top of the case
so technically both of them will be hanging out the back of the case

the reason why i want to put a cheap pci vid card in is to relave some of the stress thats on the cpu
foolish
maybe
performance gain when im trying to fix anything, or even get the latest firmware
definately
thats why no sound card will be going in
i will bump up the RAM, i forgot about that part
and a new HDD is needed since ive been using the same since i got the PC
ill be cutting alot of this case open for air
and adding a metal mesh to keep the interfearance from any disruptions
ive never done an OC
and i want to have plenty of network speed so that i can stream BluRay movies that will be stored on the pc
to any pc in the house
so all the speed that i can muster from everything the better
right?
and to power all of this
(except for the router and modem)
ill be adding a bigger PSU to the rig as well
hopefully

i will also leave a space for a N router
so when i move out it will still be in a nice singel package
then the real fun may begin

---

### Post by Rhubarb on 2009-03-10
If you run Ubuntu server edition, then your computer wouldn't have to even draw a GUI (graphical user interface), which would indeed save CPU cycles.
- As Ubuntu server edition has a command line interface (all text mode).

You may just be able to stream blu-ray movie via wireless G, certainly you'll need a big antenna for it, and hopefully your house doesn't have brick walls / thick walls, and isn't too big.
The reason why I say this, is because Wireless G runs at a maximum speed of 54MBit/s

Blu-ray movies would typically be encoded at 36 Mbit/s or perhaps even up to 48Mbit/s.
See for my sources [here]("http://en.wikipedia.org/wiki/Blu-ray_Disc_recordable") and [here]("http://ezinearticles.com/?The-Blueray-Buzz&id=1527812").

The thing about Wireless networking, be it wireless b/g/n, is that there's inherently some overhead, and depending on interference, gain, signal strength, and other environmental factors, your actual maximum wireless connection speed may very well be less than 54MBit/s.

When your trying to stream a high bit rate blu-ray video over a network that's not fast enough, you'll encounter problems playing back that stream.

I'm still not sure you'd need a fast computer to do this, as essentially all it's doing is copying over a file to a network address.

Unless of course, you wish to transcode that video into a more compressed format, so it can be streamed reliably with your slow wireless G network.
In which case you'll need a **lot** of CPU grunt to achieve this. (To the point where you'd be better off streaming DVDs rather that doing blu-rays, as DVDs have a lower bitrate).

-----

I would still consider placing your antenna a bit further away than just being ontop of your computer.

-----

Over clocking your computer can be done within ubuntu if you've got a supported CPU - I don't know exactly which CPUs are supported, as I haven't researched this.

I do know that you can overclock most CPUs by entering the BIOS as changing a few options there, like the FSB (the front-side bus), clock multipliers, ram timings, etc.

-----

Also take note that putting a mesh on the side of your PC case may introduce other problems.

While your case will be surrounded by air, there will be much less air ducting going on.  Most computer cases take air in from the front of the case, and pumps the air out via the PSU.
Doing this makes sure that all components on the motherboard, and the hard drives get a gentle breeze.
- Having a mesh as a case will likely create areas in your case that don't have air flow.  So in some cases an open / meshed case can be worse than having a closed case.

-----

Before carving up your computer to transform it into the ultimate blu-ray streaming server, I suggest you try to transfer a simple small 1 minute high bitrate (from a blu-ray video) test video to a wireless computer in your house.
As this little test will let you know if your server is up to the job of doing it or not.
From this test you could observe if there are any bottlenecks slowing down the transfer.
Bottlenecks such as CPU speed, network speed, RAM issues, hard drive speed.

-----

It sounds like a fun job there to do, having a blu-ray video server at home :)

---

### Post by hedoe on 2009-03-10
your knowledge seems endless
and thats a great idea
would i be able to use the Ubuntu releasee OS instead of the Server edition and still achive the server aspect that im looking for?
if all else fails
ill just steal another n router from ebay
and have both N and G networks broadcasting simotanusly
maybe
i have to do some research on Blade servers
might have more questions in a few

---

### Post by hedoe on 2009-03-10
and im back
yeah
blade servers out of the question
but just looking for more storage for inside the case
new questions
1: has anyone used a RAID card? for the pci slot and has SATA II headers, like this card [RAID card](http://www.newegg.com/Product/Product.aspx?Item=N82E16816104006)
i want to use 500 GB HDDs in a raid 1 array
and i figure that this card could eliminate any issues with my ageing mobo
especially the fact that it doesnt have any SATA connectors on it
2:how hard is it to set up a partition? to devide the mobo hdd and the raid array that might be provided by the RAID card?
like 500 GB for the OS, programs, updates ect. and the 1 TB for to act as the server storage? and be able to be seen on any pc with any OS?
3: is that even possible?
for the space to be seen by any OS?
4: Still need to know if the Ubuntu  PC release can still be used as a server OS

---

### Post by Rhubarb on 2009-03-10
lol yeah, blade servers are indeed out of the question :P

The Ubuntu desktop (the normal version) can be used as a server just fine.
All you need to do is to install some server applications for it (which can be done very easily).

The only downsides to using the desktop normal version, is that it'll consume a bit more RAM, and will waste a few cycles drawing the desktop, and other applications and services.  But performance-wise, it won't make that much of a big difference either way.

You can't easily combine the bandwidth of wireless G and wireless N (or indeed more than 1 network connection).  - It can be done, but not easily, and I'm not sure if this is possible with other commercial operating systems.

I have no experience with RAID cards, except that there are cheaper ones (that get your Operating System / software to do all the work), and the more expensive ones (that do everything in hardware, so it's super-quick).

You may want to do some research on file systems that are supported in Linux.  There are some nice quick ones that are excellent for big hard drives.
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by hedoe on 2009-03-11
rhubard u rock
thanks for the info

---

