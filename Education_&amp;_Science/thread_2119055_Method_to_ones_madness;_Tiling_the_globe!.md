---
title: "Method to ones madness; Tiling the globe!"
date: 2013-02-22
forum: Education &amp; Science
---

### Post by Shammai on 2013-02-22
In my new startup project, "World Of Tactics", one of the most ambitious sub-projects that I probably will ever embark upon, is a map generator which aims to tile the world.
Now before I dive into this troublesome task, I should give you an idea as to what "World Of Tactics" is going to be like. Its a tactical franchise I am developing for the Ubuntu-phone/tablet/desktop platform. 
The basic overhead will look like this:
[http://youtu.be/0uDPJ9MTi3Q?t=3m46s](http://youtu.be/0uDPJ9MTi3Q?t=3m46s)

but will maintain a lot of elements from this:
[http://youtu.be/3dbNBdrf9Cc?t=1m32s](http://youtu.be/3dbNBdrf9Cc?t=1m32s)

Now in the first example, you see that basically gameplay will be handled on a mesh grid. This will be the focus of this thread, because I am aiming at a map generator which will generate battlefields which are played on with that chess board style setup. The grandiose idea is to grab an image from a map source such as OpenStreetMags.org, generate a tile from the appropriate data, adding trees, buildings, streets, water, grass, etc; and from there, build a perpetual map that encompasses the entire globe. The possibilities of such a feat excite me to no end, and not to mention, nothing like this has really been done before.

Of course though, the first hurdle is dealing with shapes. We can not just take a globe such as this
Figure 1:
[IMG]http://derp.co.uk/f2666[/IMG]
And not expect to run into problems when generating a tile. After all, the squares at the equator are much larger than the rectangles at the poles. Thus the task of this thread is to think of solutions to this problem.
My first idea was to do something like what this gentleman is trying to do to his igloo:
Figure 2:
[IMG]http://derp.co.uk/01aa8[/IMG]
This is what I called the Tile Ribbon Method. As we see from this picture, horizontally, our tiles are in perfect alignment. Vertically however, there is obviously an issue here. Now it was late, and I had not been thinking totally straight, and I came up with what I thought would be a perfect solution:
Figure 3:
[IMG]http://derp.co.uk/35f8d[/IMG]
This is basically a 4 layered image; one colour representing its own layer. Now with the exception of green which has parts of it covered by yellow, you should be able to squint at this photo focussing on one colour, and subsequently be able to identify 6 rectangles. Now of course, The diagonals leave 12 quarters behind, however, if you line this image up with itself, you will be able to complete such squares. This would make for an interesting dynamic, and deals with the sparseness of tiles. Observe:
Figure 4:
[IMG]http://derp.co.uk/b1be6[/IMG]
if you squint your eyes, you will see that vertically, I am now aligned. The red lines link up with each other, as to the verticals. Problem solved? No; to those who have a good sense of geometry, you are obviously thinking that at some point, I am going to have a break in my alignment.

So, what then? Well now here comes the more pragmatic solutions. What is more pragmatic? Taking a chainsaw to the poles to essentially emulate this shape:
Figure: 5
[IMG]http://dug.im/26b30[/IMG]
As we see, there is no issue in tiling a cylinder, provided you are happy not having to map the north and south pole. As far as I am concerned, no one lives there, so why should I map it? The only question is, how do I take something like Figure 1, and transform it into Figure 5?
Thus this is what I call my "Orange Slice Method"
Figure 6:
[IMG]http://dug.im/795d6[/IMG]
Latitude, we would start by cutting off the tops at around 60, and for all of the longtitudes, we would pick ranges that basically only encompass ocean. For example, by my estimates on the right globe, we could get away with slicing out -17 to about  -35 (sorry iceland). On the pacific ocean side, we could do allot more. By every slice we take out, we effectively normalize the ranges, and bring our shape closer to a cylinder. While not perfect, it should suffice for our Tile Generator, eliminating much of the distortions. By the end of it, we should have a shape representing something like a barrel.

Best solution? Maybe not, after all, we just destroyed Iceland. The final solution to which I could think of was what I call the "Cubed Sphere Method"
> [Fig. 7. The cubed sphere grid mapping maps the six faces of a  cube to the surface of a sphere. The specific mapping shown here is  non-orthogonal and generates a grid that varies less than 30% in grid  cell area.]("http://www.sciencedirect.com/science/article/pii/S0021999105003967")Figure 7: 
[IMG]http://dug.im/d9aa0[/IMG]

The only problem with this is the issue of seamlessness. What this basically is, is a cube that has been turned into a sphere. The question I ask, is that when I generate my tiles, and I walk on my map to one of the corners or edges, how will the graphics engine handle it?
Thinking about it though, perhaps I can merely make the north and south poles into separate zones, that say, if you try to walk to a blue tile, you leave the current map, and load into a special northern/southern zone. Works for me!

Taking this all into account now, the things which I will have to consider are:
A) Which will be the easiest to integrate and work with openstreetmaps.org (assuming I use them)? For the orange slice method, it does seem like the basic programming would be, 
if Latitude() => 70:
    Pretend it doesnt exist!
Where as with the Cubed Sphere method, a math magician may need to be hired.
As to whether the Ribbon method could work, it seems like too much of a headache.


Perhaps I am overlooking something here though, and to that, I welcome any input you may have to give me. When the launchpad team gets around to verifying my umbrella project to all of this, I will post it up.
Until then, cheers!

---

### Post by rewyllys on 2013-02-23
Your problem is one to which cartographers have devoted several centuries of research and development.

I suggest that you look into their solutions.   Any textbook on cartography will furnish a good start.

---

### Post by rewyllys on 2013-02-25
One place to start your look at the current state of research into your problem is the Wikipedia article on "Cartographic Projections". 

Its URL is:

[https://en.wikipedia.org/wiki/Cartographic_projections](https://en.wikipedia.org/wiki/Cartographic_projections)

---

### Post by Shammai on 2013-03-10
Thinking about it; I gather that this should be pretty simple. 
 Step A: Find an ultra high resolution Height/Road map
 Step B: Determine its projection
 Step C: Determine the algorithm to its conversion from Globe to Map
 Step D: Reverse algorithm
 Step E: Apply Figure 7 algorithm, creating lines etc
 Step F: Apply algorithm to convert to cube
 Step G: Take the 6 planes, and chop them up into square images which software will use the data to convert appropriately.
 
 Now, some steps are easier than others. Additionally, a 43200x21600 map  would equal 1 square kilometer per pixel at the equator, where as my  goal would be about 1 meter per pixel at the equator. That map is about  50 mb's large. I'll double the map size just to be safe with  decompression, etc. So, * by 1000, and I get 43,200,000 x 21,600,000  pixel image, at about 100 gigabytes. Storage costs will be about 20  dollars if I mirror it [IMG]http://ubuntuforums.org/images/smilies/icon_razz.gif[/IMG].
 My work continues~

---

