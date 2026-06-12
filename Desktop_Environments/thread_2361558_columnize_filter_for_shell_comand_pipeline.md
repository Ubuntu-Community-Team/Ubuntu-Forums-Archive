---
title: "columnize filter for shell comand pipeline"
date: 2017-05-17
forum: Desktop Environments
---

### Post by Skaperen on 2017-05-17
is there a program that can take a (long, many lines) stream (of short lines) and reformat it into columns going down left first and then to the top of the next column when it reaches the bottom?

---

### Post by workinproblems on 2017-05-18
Depending on what type of text you have and where you're getting it from, you could use in Libreoffice Writer: Insert -> Section...
That automatically splits your text into 2 columns. If you want to stream it live though, I've no idea.

---

### Post by vasa1 on 2017-05-18
From the title of the thread, it appears that Skaperen wants something that works in a terminal. But even in LibreOffice Writer, isn't it Format > Columns?

I came across [https://unix.stackexchange.com/questions/81757/split-long-output-into-two-columns](https://unix.stackexchange.com/questions/81757/split-long-output-into-two-columns)

And running **column temp.txt** gives:```
$ column temp.txt
1	a	61	a	121	a	181	a	241	a
2	b	62	b	122	b	182	b	242	b
3	c	63	c	123	c	183	c	243	c
4	d	64	d	124	d	184	d	244	d
5	e	65	e	125	e	185	e	245	e
6	a	66	a	126	a	186	a	246	a
7	b	67	b	127	b	187	b	247	b
8	c	68	c	128	c	188	c	248	c
9	d	69	d	129	d	189	d	249	d
10	e	70	e	130	e	190	e	250	e
11	a	71	a	131	a	191	a	251	a
12	b	72	b	132	b	192	b	252	b
13	c	73	c	133	c	193	c	253	c
14	d	74	d	134	d	194	d	254	d
15	e	75	e	135	e	195	e	255	e
16	a	76	a	136	a	196	a	256	a
17	b	77	b	137	b	197	b	257	b
18	c	78	c	138	c	198	c	258	c
19	d	79	d	139	d	199	d	259	d
20	e	80	e	140	e	200	e	260	e
21	a	81	a	141	a	201	a	261	a
22	b	82	b	142	b	202	b	262	b
23	c	83	c	143	c	203	c	263	c
24	d	84	d	144	d	204	d	264	d
25	e	85	e	145	e	205	e	265	e
26	a	86	a	146	a	206	a	266	a
27	b	87	b	147	b	207	b	267	b
28	c	88	c	148	c	208	c	268	c
29	d	89	d	149	d	209	d	269	d
30	e	90	e	150	e	210	e	270	e
31	a	91	a	151	a	211	a	271	a
32	b	92	b	152	b	212	b	272	b
33	c	93	c	153	c	213	c	273	c
34	d	94	d	154	d	214	d	274	d
35	e	95	e	155	e	215	e	275	e
36	a	96	a	156	a	216	a	276	a
37	b	97	b	157	b	217	b	277	b
38	c	98	c	158	c	218	c	278	c
39	d	99	d	159	d	219	d	279	d
40	e	100	e	160	e	220	e	280	e
41	a	101	a	161	a	221	a	281	a
42	b	102	b	162	b	222	b	282	b
43	c	103	c	163	c	223	c	283	c
44	d	104	d	164	d	224	d	284	d
45	e	105	e	165	e	225	e	285	e
46	a	106	a	166	a	226	a	286	a
47	b	107	b	167	b	227	b	287	b
48	c	108	c	168	c	228	c	288	c
49	d	109	d	169	d	229	d	289	d
50	e	110	e	170	e	230	e	290	e
51	a	111	a	171	a	231	a	291	a
52	b	112	b	172	b	232	b	292	b
53	c	113	c	173	c	233	c	293	c
54	d	114	d	174	d	234	d	294	d
55	e	115	e	175	e	235	e	295	e
56	a	116	a	176	a	236	a	296	a
57	b	117	b	177	b	237	b	297	b
58	c	118	c	178	c	238	c	298	c
59	d	119	d	179	d	239	d	299	d
60	e	120	e	180	e	240	e	300	e

```where **temp.txt** is nothing but```
1	a
2	b
3	c
4	d
5	e
6	a
7	b
8	c
9	d
10	e
11	a
12	b
13	c
14	d
15	e
...
300	e

```

---

### Post by steeldriver on 2017-05-18
You can try the pr command:

```

$ for i in {1..12}; do printf 'Line %d\n' $i; done | pr -t -4
Line 1            Line 4            Line 7            Line 10
Line 2            Line 5            Line 8            Line 11
Line 3            Line 6            Line 9            Line 12

```

-t prevents printing of page headers/footers and -4 sets the number of columns to 4 - adjust as desired

---

### Post by Skaperen on 2017-05-26
the column command seems hopeless, there are just not enough options.  the pr command does let me control page width and number of columns.  but in a case i have there are words so big (16+ characters) that only a few columns can hold them and many words so small (2-5 characters) that there is way too much space.

i am working on my own program to do this.  i will continue the project.  it dynamically fits the input to a page so for a list of words (file names, etc), short ones will have more columns than long ones.  what can be specified is the page width and the gutter space between columns.  it then formats as many vertically aligned columns as will fit.  column width can vary within a page, too.  this program is being written in Python3 as a class (Python programs can create multiple streams) and command that processes STDIN to STDOUT through one instance of that class.

the man page for *pr* uses the term *columnate* but the word *columnize* is accepted as correct spelling by the quick reply edit area for this forum (in Firefox 53.0.2).  google has about 59000 matches for *columnate* and about 26100 matches for *columnize*.  both word lists at [FONT=courier new]/usr/share/dict/american-english[/FONT] and [FONT=courier new]/usr/share/dict/british-english[/FONT] have neither word.  which is correct?

---

