---
title: "rtorrent | rtorrent Could not read resource file: ~/.rtorrent.rc"
date: 2009-02-12
forum: General Help
---

### Post by AbsentHarvest on 2009-02-12
as the title sais... when running in CTRL +ALT F3..
Screen
rtorrent
i get that error..
rtorrent Could not read resource file: ~/.rtorrent.rc

it is infact in my home directory.

```
<!DOCTYPE html
    PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
<head>
 <title>/trunk/rtorrent/doc/rtorrent.rc - The libTorrent and rTorrent Project - Trac</title><link rel="start" href="/wiki" /><link rel="search" href="/search" /><link rel="help" href="/wiki/TracGuide" /><link rel="stylesheet" href="/trac/css/trac.css" type="text/css" /><link rel="stylesheet" href="/trac/css/code.css" type="text/css" /><link rel="stylesheet" href="/trac/css/browser.css" type="text/css" /><link rel="icon" href="/chrome/common/trac.ico" type="image/x-icon" /><link rel="shortcut icon" href="/chrome/common/trac.ico" type="image/x-icon" /><link rel="up" href="/browser/trunk/rtorrent/doc?rev=1087" title="Parent directory" /><link rel="alternate" href="/browser/trunk/rtorrent/doc/rtorrent.rc?rev=1087&amp;format=raw" title="Original Format" type="text/plain" /><style type="text/css">
</style>
 <script type="text/javascript" src="/trac/js/trac.js"></script>
</head>
<body>


<div id="banner">

<div id="header"><a id="logo" href="http://rakshasa.no"><img src="/chrome/common/trac_banner.png" width="236" height="73" alt="rakshasa.no" /></a><hr /></div>

<form id="search" action="/search" method="get">
 <div>
  <label for="proj-search">Search:</label>
  <input type="text" id="proj-search" name="q" size="10" accesskey="f" value="" />
  <input type="submit" value="Search" />
  <input type="hidden" name="wiki" value="on" />
  <input type="hidden" name="changeset" value="on" />
  <input type="hidden" name="ticket" value="on" />
 </div>
</form>



<div id="metanav" class="nav"><ul><li class="first"><a href="/login">Login</a></li><li><a href="/settings">Settings</a></li><li><a accesskey="6" href="/wiki/TracGuide">Help/Guide</a></li><li class="last"><a href="/about">About Trac</a></li></ul></div>
</div>

<div id="mainnav" class="nav"><ul><li class="first"><a accesskey="1" href="/wiki">Wiki</a></li><li><a accesskey="2" href="/timeline">Timeline</a></li><li><a accesskey="3" href="/roadmap">Roadmap</a></li><li class="active"><a href="/browser">Browse Source</a></li><li><a href="/report">View Tickets</a></li><li><a accesskey="7" href="/newticket">New Ticket</a></li><li class="last"><a accesskey="4" href="/search">Search</a></li></ul></div>
<div id="main">




<div id="ctxtnav" class="nav">
 <ul>
  <li class="first"><a href="/changeset/1013/trunk/rtorrent/doc/rtorrent.rc">
   Last Change</a></li>
  <li class="last"><a href="/log/trunk/rtorrent/doc/rtorrent.rc?rev=1087">
   Revision Log</a></li>
 </ul>
</div>


<div id="searchable">
<div id="content" class="browser">
 <h1><a class="first" title="Go to root directory" href="/browser?rev=1087">root</a><span class="sep">/</span><a title="View trunk" href="/browser/trunk?rev=1087">trunk</a><span class="sep">/</span><a title="View rtorrent" href="/browser/trunk/rtorrent?rev=1087">rtorrent</a><span class="sep">/</span><a title="View doc" href="/browser/trunk/rtorrent/doc?rev=1087">doc</a><span class="sep">/</span><a title="View rtorrent.rc" href="/browser/trunk/rtorrent/doc/rtorrent.rc?rev=1087">rtorrent.rc</a></h1>

 <div id="jumprev">
  <form action="" method="get">
   <div>
    <label for="rev">View revision:</label>
    <input type="text" id="rev" name="rev" value="1087" size="4" />
   </div>
  </form>
 </div>

 

 
  <table id="info" summary="Revision info"><tr>
    <th scope="col">
     Revision <a href="/changeset/1013">1013</a>, 3.5 kB
     (checked in by rakshasa, 1 year ago)
    </th></tr><tr>
    <td class="message"><p>
* Added support for DHT. Patch by Josef Drexler, public domain as per <br />
</p>
<blockquote>
<p>
prior agreement. <br />
</p>
</blockquote>
</td>
   </tr>
  </table>
  <div id="preview"><table class="code"><thead><tr><th class="lineno">Line</th><th class="content">&nbsp;</th></tr></thead><tbody><tr><th id="L1"><a href="#L1">1</a></th>
<td># This is an example resource file for rTorrent. Copy to</td>
</tr><tr><th id="L2"><a href="#L2">2</a></th>
<td># ~/.rtorrent.rc and enable/modify the options as needed. Remember to</td>
</tr><tr><th id="L3"><a href="#L3">3</a></th>
<td># uncomment the options you wish to enable.</td>
</tr><tr><th id="L4"><a href="#L4">4</a></th>
<td></td>
</tr><tr><th id="L5"><a href="#L5">5</a></th>
<td># Maximum and minimum number of peers to connect to per torrent.</td>
</tr><tr><th id="L6"><a href="#L6">6</a></th>
<td>min_peers = 40</td>
</tr><tr><th id="L7"><a href="#L7">7</a></th>
<td>max_peers = 100</td>
</tr><tr><th id="L8"><a href="#L8">8</a></th>
<td></td>
</tr><tr><th id="L9"><a href="#L9">9</a></th>
<td># Same as above but for seeding completed torrents (-1 = same as downloading)</td>
</tr><tr><th id="L10"><a href="#L10">10</a></th>
<td>min_peers_seed = 10</td>
</tr><tr><th id="L11"><a href="#L11">11</a></th>
<td>max_peers_seed = 50</td>
</tr><tr><th id="L12"><a href="#L12">12</a></th>
<td></td>
</tr><tr><th id="L13"><a href="#L13">13</a></th>
<td># Maximum number of simultanious uploads per torrent.</td>
</tr><tr><th id="L14"><a href="#L14">14</a></th>
<td>max_uploads = 15</td>
</tr><tr><th id="L15"><a href="#L15">15</a></th>
<td></td>
</tr><tr><th id="L16"><a href="#L16">16</a></th>
<td># Global upload and download rate in KiB. &#34;0&#34; for unlimited.</td>
</tr><tr><th id="L17"><a href="#L17">17</a></th>
<td>download_rate = &#34;0&#34;</td>
</tr><tr><th id="L18"><a href="#L18">18</a></th>
<td>upload_rate = &#34;0&#34;</td>
</tr><tr><th id="L19"><a href="#L19">19</a></th>
<td></td>
</tr><tr><th id="L20"><a href="#L20">20</a></th>
<td># Default directory to save the downloaded torrents.</td>
</tr><tr><th id="L21"><a href="#L21">21</a></th>
<td>#directory = /Downloads</td>
</tr><tr><th id="L22"><a href="#L22">22</a></th>
<td></td>
</tr><tr><th id="L23"><a href="#L23">23</a></th>
<td># Default session directory. Make sure you don't run multiple instance</td>
</tr><tr><th id="L24"><a href="#L24">24</a></th>
<td># of rtorrent using the same session directory. Perhaps using a</td>
</tr><tr><th id="L25"><a href="#L25">25</a></th>
<td># relative path?</td>
</tr><tr><th id="L26"><a href="#L26">26</a></th>
<td>session = ./session</td>
</tr><tr><th id="L27"><a href="#L27">27</a></th>
<td></td>
</tr><tr><th id="L28"><a href="#L28">28</a></th>
<td># Watch a directory for new torrents, and stop those that have been</td>
</tr><tr><th id="L29"><a href="#L29">29</a></th>
<td># deleted.</td>
</tr><tr><th id="L30"><a href="#L30">30</a></th>
<td>schedule = watch_directory,5,5,load_start=./watch/*.torrent</td>
</tr><tr><th id="L31"><a href="#L31">31</a></th>
<td>schedule = untied_directory,5,5,stop_untied=</td>
</tr><tr><th id="L32"><a href="#L32">32</a></th>
<td></td>
</tr><tr><th id="L33"><a href="#L33">33</a></th>
<td># Close torrents when diskspace is low.</td>
</tr><tr><th id="L34"><a href="#L34">34</a></th>
<td>schedule = low_diskspace,5,60,close_low_diskspace=100M</td>
</tr><tr><th id="L35"><a href="#L35">35</a></th>
<td></td>
</tr><tr><th id="L36"><a href="#L36">36</a></th>
<td># Stop torrents when reaching upload ratio in percent,</td>
</tr><tr><th id="L37"><a href="#L37">37</a></th>
<td># when also reaching total upload in bytes, or when</td>
</tr><tr><th id="L38"><a href="#L38">38</a></th>
<td># reaching final upload ratio in percent.</td>
</tr><tr><th id="L39"><a href="#L39">39</a></th>
<td># example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0</td>
</tr><tr><th id="L40"><a href="#L40">40</a></th>
<td>schedule = ratio,60,60,&#34;stop_on_ratio=200,200M,2000&#34;</td>
</tr><tr><th id="L41"><a href="#L41">41</a></th>
<td></td>
</tr><tr><th id="L42"><a href="#L42">42</a></th>
<td># The ip address reported to the tracker.</td>
</tr><tr><th id="L43"><a href="#L43">43</a></th>
<td>ip = 127.0.0.1</td>
</tr><tr><th id="L44"><a href="#L44">44</a></th>
<td>ip = rakshasa.no</td>
</tr><tr><th id="L45"><a href="#L45">45</a></th>
<td></td>
</tr><tr><th id="L46"><a href="#L46">46</a></th>
<td># The ip address the listening socket and outgoing connections is</td>
</tr><tr><th id="L47"><a href="#L47">47</a></th>
<td># bound to.</td>
</tr><tr><th id="L48"><a href="#L48">48</a></th>
<td>bind = 127.0.0.1</td>
</tr><tr><th id="L49"><a href="#L49">49</a></th>
<td>bind = rakshasa.no</td>
</tr><tr><th id="L50"><a href="#L50">50</a></th>
<td></td>
</tr><tr><th id="L51"><a href="#L51">51</a></th>
<td># Port range to use for listening.</td>
</tr><tr><th id="L52"><a href="#L52">52</a></th>
<td>port_range = 6890-6999</td>
</tr><tr><th id="L53"><a href="#L53">53</a></th>
<td></td>
</tr><tr><th id="L54"><a href="#L54">54</a></th>
<td># Start opening ports at a random position within the port range.</td>
</tr><tr><th id="L55"><a href="#L55">55</a></th>
<td>port_random = no</td>
</tr><tr><th id="L56"><a href="#L56">56</a></th>
<td></td>
</tr><tr><th id="L57"><a href="#L57">57</a></th>
<td># Check hash for finished torrents. Might be usefull until the bug is</td>
</tr><tr><th id="L58"><a href="#L58">58</a></th>
<td># fixed that causes lack of diskspace not to be properly reported.</td>
</tr><tr><th id="L59"><a href="#L59">59</a></th>
<td>check_hash = no</td>
</tr><tr><th id="L60"><a href="#L60">60</a></th>
<td></td>
</tr><tr><th id="L61"><a href="#L61">61</a></th>
<td># Set whetever the client should try to connect to UDP trackers.</td>
</tr><tr><th id="L62"><a href="#L62">62</a></th>
<td>use_udp_trackers = yes</td>
</tr><tr><th id="L63"><a href="#L63">63</a></th>
<td></td>
</tr><tr><th id="L64"><a href="#L64">64</a></th>
<td># Alternative calls to bind and ip that should handle dynamic ip's.</td>
</tr><tr><th id="L65"><a href="#L65">65</a></th>
<td>schedule = ip_tick,0,1800,ip=rakshasa</td>
</tr><tr><th id="L66"><a href="#L66">66</a></th>
<td>schedule = bind_tick,0,1800,bind=rakshasa</td>
</tr><tr><th id="L67"><a href="#L67">67</a></th>
<td></td>
</tr><tr><th id="L68"><a href="#L68">68</a></th>
<td># Encryption options, set to none (default) or any combination of the following:</td>
</tr><tr><th id="L69"><a href="#L69">69</a></th>
<td># allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext</td>
</tr><tr><th id="L70"><a href="#L70">70</a></th>
<td> allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext</td>
</tr><tr><th id="L71"><a href="#L71">71</a></th>
<td># The example value allows incoming encrypted connections, starts unencrypted</td>
</tr><tr><th id="L72"><a href="#L72">72</a></th>
<td># outgoing connections but retries with encryption if they fail, preferring</td>
</tr><tr><th id="L73"><a href="#L73">73</a></th>
<td># plaintext to RC4 encryption after the encrypted handshake</td>
</tr><tr><th id="L74"><a href="#L74">74</a></th>
<td>#</td>
</tr><tr><th id="L75"><a href="#L75">75</a></th>
<td> encryption = allow_incoming,enable_retry,prefer_plaintext</td>
</tr><tr><th id="L76"><a href="#L76">76</a></th>
<td></td>
</tr><tr><th id="L77"><a href="#L77">77</a></th>
<td># Enable DHT support for trackerless torrents or when all trackers are down.</td>
</tr><tr><th id="L78"><a href="#L78">78</a></th>
<td># May be set to &#34;disable&#34; (completely disable DHT), &#34;off&#34; (do not start DHT),</td>
</tr><tr><th id="L79"><a href="#L79">79</a></th>
<td># &#34;auto&#34; (start and stop DHT as needed), or &#34;on&#34; (start DHT immediately).</td>
</tr><tr><th id="L80"><a href="#L80">80</a></th>
<td># The default is &#34;off&#34;. For DHT to work, a session directory must be defined.</td>
</tr><tr><th id="L81"><a href="#L81">81</a></th>
<td># </td>
</tr><tr><th id="L82"><a href="#L82">82</a></th>
<td> dht = auto</td>
</tr><tr><th id="L83"><a href="#L83">83</a></th>
<td></td>
</tr><tr><th id="L84"><a href="#L84">84</a></th>
<td> UDP port to use for DHT. </td>
</tr><tr><th id="L85"><a href="#L85">85</a></th>
<td># </td>
</tr><tr><th id="L86"><a href="#L86">86</a></th>
<td> dht_port = 6881</td>
</tr><tr><th id="L87"><a href="#L87">87</a></th>
<td></td>
</tr><tr><th id="L88"><a href="#L88">88</a></th>
<td># Enable peer exchange (for torrents not marked private)</td>
</tr><tr><th id="L89"><a href="#L89">89</a></th>
<td>#</td>
</tr><tr><th id="L90"><a href="#L90">90</a></th>
<td> peer_exchange = yes</td>
</tr><tr><th id="L91"><a href="#L91">91</a></th>
<td></td>
</tr><tr><th id="L92"><a href="#L92">92</a></th>
<td>#</td>
</tr><tr><th id="L93"><a href="#L93">93</a></th>
<td># Do not modify the following parameters unless you know what you're doing.</td>
</tr><tr><th id="L94"><a href="#L94">94</a></th>
<td>#</td>
</tr><tr><th id="L95"><a href="#L95">95</a></th>
<td></td>
</tr><tr><th id="L96"><a href="#L96">96</a></th>
<td># Hash read-ahead controls how many MB to request the kernel to read</td>
</tr><tr><th id="L97"><a href="#L97">97</a></th>
<td># ahead. If the value is too low the disk may not be fully utilized,</td>
</tr><tr><th id="L98"><a href="#L98">98</a></th>
<td># while if too high the kernel might not be able to keep the read</td>
</tr><tr><th id="L99"><a href="#L99">99</a></th>
<td># pages in memory thus end up trashing.</td>
</tr><tr><th id="L100"><a href="#L100">100</a></th>
<td>hash_read_ahead = 10</td>
</tr><tr><th id="L101"><a href="#L101">101</a></th>
<td></td>
</tr><tr><th id="L102"><a href="#L102">102</a></th>
<td># Interval between attempts to check the hash, in milliseconds.</td>
</tr><tr><th id="L103"><a href="#L103">103</a></th>
<td>#ash_interval = 100</td>
</tr><tr><th id="L104"><a href="#L104">104</a></th>
<td></td>
</tr><tr><th id="L105"><a href="#L105">105</a></th>
<td># Number of attempts to check the hash while using the mincore status,</td>
</tr><tr><th id="L106"><a href="#L106">106</a></th>
<td># before forcing. Overworked systems might need lower values to get a</td>
</tr><tr><th id="L107"><a href="#L107">107</a></th>
<td># decent hash checking rate.</td>
</tr><tr><th id="L108"><a href="#L108">108</a></th>
<td>hash_max_tries = 10</td>
</tr></tbody></table>
  </div>

 <div id="help">
  <strong>Note:</strong> See <a href="/wiki/TracBrowser">TracBrowser</a> for help on using the browser.
 </div>

  <div id="anydiff">
   <form action="/anydiff" method="get">
    <div class="buttons">
     <input type="hidden" name="new_path" value="/trunk/rtorrent/doc/rtorrent.rc" />
     <input type="hidden" name="old_path" value="/trunk/rtorrent/doc/rtorrent.rc" />
     <input type="hidden" name="new_rev" value="1087" />
     <input type="hidden" name="old_rev" value="1087" />
     <input type="submit" value="View changes..." title="Prepare an Arbitrary Diff" />
    </div>
   </form>
  </div>

</div>
</div>
<script type="text/javascript">searchHighlight()</script>
<div id="altlinks"><h3>Download in other formats:</h3><ul><li class="first last"><a href="/browser/trunk/rtorrent/doc/rtorrent.rc?rev=1087&amp;format=raw">Original Format</a></li></ul></div>

</div>

<div id="footer">
 <hr />
 <a id="tracpowered" href="http://trac.edgewall.org/"><img src="/trac/trac_logo_mini.png" height="30" width="107"
   alt="Trac Powered"/></a>
 <p class="right">
  The sodden squirrels belong to Jari Sundell <br /><a href="http://rakshasa.no/">http://rakshasa.no/</a>
 </p>
</div>



 </body>
</html>

```

I also have a Torrents Folder -- Complete, Downloading and Torrent Files - Auto in my Home directory... Where am I going wrong?

---

### Post by Dr Small on 2009-02-12
Well, I can tell you that isn't the ~/.rtorrentrc file.

---

### Post by AbsentHarvest on 2009-02-12
you're right.. i think it's just the rtorrent.rc not the .rtorrent.rc................... regardless i found this by gedit ~/.rtorrent.rc so that's where it's suppose to be and that's what i get..... hmmm this is very confusing.

---

### Post by chitowner2 on 2010-12-10
see here:
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

In Ubuntu, the sample rtorrent configuration file is hiding at /usr/share/doc/rtorrent/examples/rtorrent.rc. Copy one for your own perusal, and give it the proper hidden file prefix.
cp /usr/share/doc/rtorrent/examples/rtorrent.rc ~/.rtorrent.rc



:)
CT

---

