# Typstio

A library for generating and compiling `Typst` code. Its core component is `ContentWriter`, which aggregates all visual elements (text, tables, blocks, etc.). This enables seamless integration of report, schedule, list, and other document generation capabilities into your projects.

The document description logic mirrors `Typst` syntax one-to-one, preserving the same linear structure. As a result, developers familiar with Typst can adopt this solution with minimal effort.

### Sample

```C#
var document = new ContentWriter();
var image = new Image("profile.jpg", width: "20%");

document.Write(new Figure(image, "About me"));
document.WriteEmptyBlock();

document.Write(CreateUserTable());
document.WriteEmptyBlock();

document.Write(new Box(c => c.WriteString("Hello from Box"), new Rgb("#ff4136")));

Table CreateUserTable()
{
    var items = new Content[]
    {
        _ => { },
        c => c.Write(new Strong("Name")),
        c => c.Write(new Strong("Phone")),
        
        c => c.WriteString("1"),
        c => c.WriteString("Sparrow"),
        c => c.WriteString("+79531345309").Linebreak()
              .WriteString("+89231365311")
    };
    
    return new Table(("auto", "1fr", "1fr"), items, inset: "10pt", align: "horizon");
}
```

#### Output

![Sample-1](./static/sample1.png)
