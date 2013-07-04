CSS-Grid
========

CSS3 Flex-Box based Grid System

@font-size: 16; // Your basic font-size
@em: @font-size*1em;
@column: 48; //width of columns
@gutter: 36; // width of gutters
.parent () {  //required until there is a :parent Selector
    display: flex;
    flex-flow: row wrap;
    display: -webkit-flex;
    -webkit-flex-flow: row wrap;
}
.child (@cols:1; @margin: 1;) {//first argument: number of columns; second argument: number of gutters (0 for an element containing other columns)
    margin: 0 (@gutter / 2 / @em * @margin);
    flex: @cols 1 (@cols * (@column + @gutter) - (@gutter * @margin)) / @em;
    -webkit-flex: @cols 1 (@cols * (@column + @gutter) - (@gutter * @margin)) / @em;
}
body { //custom zoom
    @media screen {
    font-size: (@font-size + 2) / @em;
    @media (min-width: 80em) {font-size: (@font-size + 4) / @em;}
    @media (min-width: 120em) {font-size: (@font-size + 6) / @em;}
    }
}

// Examples

body {
    .parent(); //set body as parent element for flex based childs
}
div.example {
    .child(6); //child element with width of 5 columns
}
div.containing {
    .child(6;0) //silbing element of div.example with same width, containing childs
}
div.containing p {
    .child(3); //child element of div.containing with half width
}

// Related HTML Code

<body>
  <div class="example">This is a div</div>
  <div class="containing">
    <p>This is a half-width child element</p>
    <p>Another child</p>
  </div>
  <div class="example">Another div</div>
</body>
