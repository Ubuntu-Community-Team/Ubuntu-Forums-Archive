---
title: "sci-buntu"
date: 2009-06-07
forum: Education &amp; Science
---

### Post by uberdonkey5 on 2009-06-07
I know they have edubuntu, but that seems to be geared towards kids games. Anyone seen or thought of creating a distro for scientists? It's pretty easy to remove packages, but would be good if we could get a version with:

- fully functional bibliography software
- latex software
- some programming software
- statistical (univariate and multivariate) software
- modelling software
- GIS

?

---

### Post by uberdonkey5 on 2009-06-07
oops...

should have searched first...

[http://www.debianadmin.com/scibuntu-ubuntu-linux-for-scientist-and-science-students-installation-with-screenshots.html](http://www.debianadmin.com/scibuntu-ubuntu-linux-for-scientist-and-science-students-installation-with-screenshots.html)

any thoughts on scibuntu? As far as I can see it doesn't really fulfil all my needs.

---

### Post by InfernalNeutrino on 2009-06-07
Honestly, I would be happier if the focus was given to making sure that the latest stable packages of interest were in the repositories, rather than trying to maintain yet another sub-distro. With any decent package manager it is easy to search for and add packages, which seems (IMHO) to render the overhead involved in maintaining a distro unnecessary. Between that and the fact that different areas of science have different needs makes me believe that the focus should be on maintaining the packages, rather than a distro. Again though, it's just my opinion.

---

### Post by gunksta on 2009-06-07
Projects like edubuntu struggle with a lack of focus / direction. Who is the target audience? An educational suite that is suitable for elementary school children is useless to a high-schooler.

I fear something like sci-buntu would struggle with the same challenge - Who is the target audience? I'm a social scientist. LATEX, R, Gnumeric, etc. are all things that I find useful. (Have fun getting r-recommended on a CD alongside a basic, usable Ubuntu installation) But, to really meet my needs I would also need postgres or mysql (postgres is probably better because it's so easy to work with GIS data). 

But if you compare my needs to a molecular biologist, I suspect they are different. I don't know what a molecular biologist really needs, but suspect there are tools that are very useful to them. In contrast, a first year college student interested in majoring in physics needs something else entirely.

sci-buntu would struggle because I don't know who should use sci-buntu.

There are some discussions in this forum on different tools to use for different realms of science. I think the best thing to do is to make sure it's easy to google for information detailing what tools exist on linux that are useful/relevant to different fields of science. Anyone who is really engaged in scientific endeavors is probably capable of reading this sort of material and making good decisions for themselves.

---

### Post by machoo02 on 2009-06-08
I agree with gunksta as well: the needs of varying branches of science will be very different from one another.  The easiest way, IMHO, to have a 'Scibuntu' would be to make sure that the [Ubuntu Wiki Science page]("https://help.ubuntu.com/community/UbuntuScience") is complete and up to date, and to make sure that the latest versions of the software listed on the science page are in the repos.  Metapackages (e.g., ubuntu-science-biology, ubuntu-science-physics, etc) that depended on a number of commonly used software for that particular branch of science would make installing a science-oriented setup somewhat less complicated as well.

---

### Post by akniss on 2009-06-08
> **machoo02 said:**
>   Metapackages (e.g., ubuntu-science-biology, ubuntu-science-physics, etc) that depended on a number of commonly used software for that particular branch of science would make installing a science-oriented setup somewhat less complicated as well.

I really like the metapackage idea.  It makes much more sense than a "science" sub-distribution.  I'm quite happy with the base Ubuntu, and really see no need for Sci-buntu since I'm sure there would be many packages installed that I don't need and some that I need that aren't installed.  But a metapackage designed for ecologists, or physics, etc. makes a lot of sense, provided they are maintained by someone within the field that knows what type of software is useful within that discipline.

---

### Post by gunksta on 2009-06-10
As much as I like the idea of metapackages, I wonder how new (noob) users would find them. Our current graphical tools make it difficult to discover these package sets. Yet, the idea of meta-packages that can install commonly used packs of software, pre-selected by people knowledgeable about both Ubuntu and science/art/what-have-you could make it much easier for new users to get into and use Ubuntu.

As much as I like our large, free-ranging software repositories; they are difficult for new users to navigate/use. My girlfriend has tried to use Add/Remove and Synaptic and has had a couple of problems.


[LIST=1]
[*]She has installed a couple of programs, and not been able to find them because they are CLI-only. This really should be more clearly marked.
[*]She has installed software that is no longer being actively developed, which I tend to recommend against using unless you can't find a suitable alternative (for me that would be Unison). Current tools such as Synaptic don't indicate if a package has been updated since the last release, or provide any other indication as to a project's activity level.
[/LIST]

The idea of domain-specific meta-packages could be a really neat way to balance the need to not cull all of the useful but crufty abandonware from the repositories, while making it easier for newer users to quickly get a usable system with the sort of software they want/need.

Plus, if a new tool comes out in the future that is relevant, users can be assured they will automatically pick it up, and not have to discover it for themselves.

The biggest question, is how and where to set up these metapackages so users find them as easily as they do the plethora of packages and metapackages that exist today. For these to really be useful they must be incredibly obvious and very, very clear about what they do.

---

### Post by gunksta on 2009-06-10
I got curious, so I went over to Ubuntu Brainstorm and did a search for "meta". I pulled up some interesting ideas, but nothing similar to the domain specific meta-packages that machoo02 suggested.

The more I think about it, the more I think that domain-specific meta-packages (for science, art, writing, etc.) could really be a super cool thing. It could make Linux more accessible and help people discover really cool software.

Since it was macoo002's idea, I'll let him submit it to Brainstorm. Let me know when you do and I'll vote for it immediately.

---

### Post by phaed on 2009-06-10
I'm pretty much in agreement with the others.  Maintaining an up-to-date list of applications, and maintaining up-to-date packages, and allowing people to choose the applications that they need, is much more useful (and less time and resource consuming) than maintaining a derivative distro.  

Actually, spending some time writing tutorials on how to use the applications would be orders of magnitude more useful.

---

