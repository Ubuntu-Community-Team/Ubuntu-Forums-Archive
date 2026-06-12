---
title: "Compilation failed for an R add-on package"
date: 2014-06-23
forum: Education &amp; Science
---

### Post by lobby2 on 2014-06-23
[FONT=verdana][COLOR=#000000][SIZE=2]Hi all, I am trying to compile on the Debian Shell a package which contains C++ code that some other R packages call into. Actuatty, this package is a collection of C++ classes for Bayesian computation. 
I run the command:[/SIZE]
[/COLOR][/FONT][INDENT]```
R CMD INSTALL
```[/INDENT]

[COLOR=#000000][FONT=Arial][FONT=verdana]but this throws me the following error:[/FONT]
[/FONT][/COLOR]
```
[COLOR=#2B91AF]Models[/COLOR]/HMM/[COLOR=#2B91AF]Clickstream[/COLOR]/[COLOR=#2B91AF]Session[/COLOR].cpp:[COLOR=#800000]13[/COLOR]:[COLOR=#800000]21[/COLOR]: error: [COLOR=#00008B]no[/COLOR] matching [COLOR=#00008B]function[/COLOR] [COLOR=#00008B]for[/COLOR] call to &#8216;BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]>::[COLOR=#2B91AF]TimeSeries[/COLOR]([COLOR=#00008B]const[/COLOR] std::vector<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]>, std::allocator<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]> > >&, [COLOR=#00008B]bool[/COLOR])&#8217;
[COLOR=#2B91AF]Models[/COLOR]/HMM/[COLOR=#2B91AF]Clickstream[/COLOR]/[COLOR=#2B91AF]Session[/COLOR].cpp:[COLOR=#800000]13[/COLOR]:[COLOR=#800000]21[/COLOR]: note: candidates are:
[COLOR=#2B91AF]In[/COLOR] file included [COLOR=#00008B]from[/COLOR] ../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]MarkovModel[/COLOR].hpp:[COLOR=#800000]34[/COLOR]:[COLOR=#800000]0[/COLOR],
                 [COLOR=#00008B]from[/COLOR] ../inst/include/[COLOR=#2B91AF]Models[/COLOR]/HMM/[COLOR=#2B91AF]Clickstream[/COLOR]/[COLOR=#2B91AF]Event[/COLOR].hpp:[COLOR=#800000]4[/COLOR],
                 [COLOR=#00008B]from[/COLOR] ../inst/include/[COLOR=#2B91AF]Models[/COLOR]/HMM/[COLOR=#2B91AF]Clickstream[/COLOR]/[COLOR=#2B91AF]Session[/COLOR].hpp:[COLOR=#800000]4[/COLOR],
                 [COLOR=#00008B]from[/COLOR] [COLOR=#2B91AF]Models[/COLOR]/HMM/[COLOR=#2B91AF]Clickstream[/COLOR]/[COLOR=#2B91AF]Session[/COLOR].cpp:[COLOR=#800000]1[/COLOR]:
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]244[/COLOR]:[COLOR=#800000]3[/COLOR]: note: BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]<D>::[COLOR=#2B91AF]TimeSeries[/COLOR]([COLOR=#00008B]const[/COLOR] BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]<D>&) [[COLOR=#00008B]with[/COLOR] D = BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]; BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]<D> = BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]>]
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]244[/COLOR]:[COLOR=#800000]3[/COLOR]: note:   candidate expects [COLOR=#800000]1[/COLOR] argument, [COLOR=#800000]2[/COLOR] provided
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]55[/COLOR]:[COLOR=#800000]5[/COLOR]: note: [COLOR=#00008B]template[/COLOR]<[COLOR=#00008B]class[/COLOR] [COLOR=#2B91AF]FwdIt[/COLOR]> BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]::[COLOR=#2B91AF]TimeSeries[/COLOR]([COLOR=#2B91AF]FwdIt[/COLOR], [COLOR=#2B91AF]FwdIt[/COLOR], [COLOR=#00008B]bool[/COLOR], [COLOR=#00008B]bool[/COLOR], [COLOR=#00008B]const[/COLOR] [COLOR=#00008B]string[/COLOR]&)
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]55[/COLOR]:[COLOR=#800000]5[/COLOR]: note:   [COLOR=#00008B]template[/COLOR] argument deduction/substitution failed:
[COLOR=#2B91AF]Models[/COLOR]/HMM/[COLOR=#2B91AF]Clickstream[/COLOR]/[COLOR=#2B91AF]Session[/COLOR].cpp:[COLOR=#800000]13[/COLOR]:[COLOR=#800000]21[/COLOR]: note:   deduced conflicting types [COLOR=#00008B]for[/COLOR] parameter &#8216;[COLOR=#2B91AF]FwdIt[/COLOR]&#8217; (&#8216;std::vector<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]>, std::allocator<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]> > >&#8217; [COLOR=#00008B]and[/COLOR] &#8216;[COLOR=#00008B]bool[/COLOR]&#8217;)
[COLOR=#2B91AF]In[/COLOR] file included [COLOR=#00008B]from[/COLOR] ../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]MarkovModel[/COLOR].hpp:[COLOR=#800000]34[/COLOR]:[COLOR=#800000]0[/COLOR],
                 [COLOR=#00008B]from[/COLOR] ../inst/include/[COLOR=#2B91AF]Models[/COLOR]/HMM/[COLOR=#2B91AF]Clickstream[/COLOR]/[COLOR=#2B91AF]Event[/COLOR].hpp:[COLOR=#800000]4[/COLOR],
                 [COLOR=#00008B]from[/COLOR] ../inst/include/[COLOR=#2B91AF]Models[/COLOR]/HMM/[COLOR=#2B91AF]Clickstream[/COLOR]/[COLOR=#2B91AF]Session[/COLOR].hpp:[COLOR=#800000]4[/COLOR],
                 [COLOR=#00008B]from[/COLOR] [COLOR=#2B91AF]Models[/COLOR]/HMM/[COLOR=#2B91AF]Clickstream[/COLOR]/[COLOR=#2B91AF]Session[/COLOR].cpp:[COLOR=#800000]1[/COLOR]:
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]233[/COLOR]:[COLOR=#800000]3[/COLOR]: note: BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]<D>::[COLOR=#2B91AF]TimeSeries[/COLOR]([COLOR=#00008B]const[/COLOR] [COLOR=#2B91AF]vec_t[/COLOR]&, [COLOR=#00008B]bool[/COLOR], [COLOR=#00008B]const[/COLOR] [COLOR=#00008B]string[/COLOR]&) [[COLOR=#00008B]with[/COLOR] D = BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]; BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]<D>::[COLOR=#2B91AF]vec_t[/COLOR] = std::vector<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]>, std::allocator<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]> > >; std::[COLOR=#00008B]string[/COLOR] = std::basic_string[COLOR=#800000]<char>[/COLOR]]
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]233[/COLOR]:[COLOR=#800000]3[/COLOR]: note:   [COLOR=#00008B]no[/COLOR] known conversion [COLOR=#00008B]for[/COLOR] argument [COLOR=#800000]1[/COLOR] [COLOR=#00008B]from[/COLOR] &#8216;[COLOR=#00008B]const[/COLOR] std::vector<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]>, std::allocator<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]> > >&#8217; to &#8216;std::vector<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]>, std::allocator<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]> > >&&#8217;
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]193[/COLOR]:[COLOR=#800000]3[/COLOR]: note: BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]<D>::[COLOR=#2B91AF]TimeSeries[/COLOR]([COLOR=#00008B]const[/COLOR] BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<T, [COLOR=#00008B]true[/COLOR]>&, [COLOR=#00008B]const[/COLOR] [COLOR=#00008B]string[/COLOR]&) [[COLOR=#00008B]with[/COLOR] D = BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]; std::[COLOR=#00008B]string[/COLOR] = std::basic_string[COLOR=#800000]<char>[/COLOR]]
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]193[/COLOR]:[COLOR=#800000]3[/COLOR]: note:   [COLOR=#00008B]no[/COLOR] known conversion [COLOR=#00008B]for[/COLOR] argument [COLOR=#800000]1[/COLOR] [COLOR=#00008B]from[/COLOR] &#8216;[COLOR=#00008B]const[/COLOR] std::vector<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]>, std::allocator<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]> > >&#8217; to &#8216;[COLOR=#00008B]const[/COLOR] BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]>&&#8217;
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]185[/COLOR]:[COLOR=#800000]3[/COLOR]: note: BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]<D>::[COLOR=#2B91AF]TimeSeries[/COLOR]([COLOR=#00008B]const[/COLOR] D&, [COLOR=#00008B]const[/COLOR] [COLOR=#00008B]string[/COLOR]&) [[COLOR=#00008B]with[/COLOR] D = BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]; std::[COLOR=#00008B]string[/COLOR] = std::basic_string[COLOR=#800000]<char>[/COLOR]]
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]185[/COLOR]:[COLOR=#800000]3[/COLOR]: note:   [COLOR=#00008B]no[/COLOR] known conversion [COLOR=#00008B]for[/COLOR] argument [COLOR=#800000]1[/COLOR] [COLOR=#00008B]from[/COLOR] &#8216;[COLOR=#00008B]const[/COLOR] std::vector<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]>, std::allocator<BOOM::[COLOR=#2B91AF]Ptr[/COLOR]<BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]> > >&#8217; to &#8216;[COLOR=#00008B]const[/COLOR] BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]&&#8217;
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]174[/COLOR]:[COLOR=#800000]3[/COLOR]: note: BOOM::[COLOR=#2B91AF]TimeSeries[/COLOR]<D>::[COLOR=#2B91AF]TimeSeries[/COLOR]([COLOR=#00008B]const[/COLOR] [COLOR=#00008B]string[/COLOR]&) [[COLOR=#00008B]with[/COLOR] D = BOOM::[COLOR=#2B91AF]Clickstream[/COLOR]::[COLOR=#2B91AF]Event[/COLOR]; std::[COLOR=#00008B]string[/COLOR] = std::basic_string[COLOR=#800000]<char>[/COLOR]]
../inst/include/[COLOR=#2B91AF]Models[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR]/[COLOR=#2B91AF]TimeSeries[/COLOR].hpp:[COLOR=#800000]174[/COLOR]:[COLOR=#800000]3[/COLOR]: note:   candidate expects [COLOR=#800000]1[/COLOR] argument, [COLOR=#800000]2[/COLOR] provided
make: *** [[COLOR=#2B91AF]Models[/COLOR]/HMM/[COLOR=#2B91AF]Clickstream[/COLOR]/[COLOR=#2B91AF]Session[/COLOR].o] [COLOR=#2B91AF]Error[/COLOR] [COLOR=#800000]1[/COLOR]
ERROR: compilation failed [COLOR=#00008B]for[/COLOR] [COLOR=#00008B]package[/COLOR] &#8216;[COLOR=#2B91AF]Boom[/COLOR]&#8217;

```
[COLOR=#000000][FONT=Arial]
[FONT=verdana]I am not able to get around the problem. Any help would be appreciated.[/FONT][/FONT][/COLOR]

---

### Post by rewyllys on 2014-06-24
What is the name of the package you're trying to install? (Yes, it's clearly something to do with time-series, but specifically, which time-series package?)

---

### Post by lobby2 on 2014-06-24
Hi rewyllys, thanks for your reply.

The name of the package is Boom, retrieved from there: [https://sites.google.com/site/stevethebayesian/googlepageforstevenlscott/boom](https://sites.google.com/site/stevethebayesian/googlepageforstevenlscott/boom)

---

