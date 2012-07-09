As of 7/6/12, this repository contains the following sections of NY State Law

* [Section 24 of the Tax law.](http://public.leginfo.state.ny.us/LAWSSEAF.cgi?QUERYTYPE=LAWS+&QUERYDATA=$$TAX24$$@TXTAX024+&LIST=LAW+&BROWSER=BROWSER+&TOKEN=42224016+&TARGET=VIEW) 
* [Article Part 1, Title A, Articles 1, 5, and 10 of the Penal law.](http://public.leginfo.state.ny.us/LAWSSEAF.cgi?QUERYTYPE=LAWS+&QUERYDATA=@PLPEN0P1TA+&LIST=LAW+&BROWSER=BROWSER+&TOKEN=42224016+&TARGET=VIEW)

Here are a few of the conventions I'm currently following and the reasoning behind it.

**1. Breaking consolidated laws down to the paragraph level.**

Bills in the New York State legislature are often ammending existing law. Some bills create entirely new supersections of law (often categorized as "unconsolidated laws" in the existing corpus), but those are relatively rare.

A typical bill consists of a stated purpose followed by a series of changes to marked-up paragraphs. A bill lets you know which text is added to the paragraph in question by rendering it in all-caps typography. Text being removed from a law is often rendered with strike-through typography and enclosed in brackets. Take [S4199](http://open.nysenate.gov/legislation/bill/S4199-2011) as an example.

For the purpose of developing a standard for storing NY Legislation in version control, I think it makes sense to break the document into the most granular units possible. Because bills are, by definition, directions for amending, adding and deleting paragraphs, the paragraph seems like a natural choice.

**2. Paragraph numbers are used as filenames**

Nearly every element in the NY Law document tree is indexed in some way (e.g. The penal code alone is divided into Parts, Titles, Articles, Sections, and then paragraphs, all of which have a sortable identifier such as A-Z or 1-99 or 1.0-99.99, etc.). By comparison, most elements at the paragraph level do not have titles. Therefore, it makes sense to use the sortable identifier for the filename rather than a title (such as "The Empire State Film Production Credit").

**3. Titles for all groupings are stored in "TITLE.md files.**

As I said earlier, titles appear somewhat inconsistently throughout the corpus. TITLE.md files each contain the title for the grouping in which they appear. If there is no title for a grouping, then there is no title.md file. 

**4. Grouping Topmatter - TOPMATTER.md.**

Some groupings (whether it be a group of titles, articles, parts, sections, or paragraphs) contain an introductory paragraph or two. This text appers in TOPMATTER.md files where appropriate.

**4. Grouping Prefixes - PREFIX.md.**

The only grouping that appears to be standard acros all of the laws is the "section." As such, folders/directories representing sections of the law have a file simply named "SECTION". These files have no content. As I mentioned earlier, paragraph filenames are composed based on that paragraph's number within the parent group (usually a section, but sometimes a subdivision of a section).

For groupings that have non-standard prefixes (e.g. Parts, Titles, Articles, etc.), those directories contain a PREFIX.md file containing the appropriate text string.

**5. Use of Markdown**

I'm using markdown to store text because I feel like it's the most accessible for someone who is accessing the laws through a git repo rather than a specialized interface developed by us. Because there are so many libraries for converting markdown to other formats, it should be easy for us to serialize the directory into xml, json, HTML, or whatever format we need in the future.