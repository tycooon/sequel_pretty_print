# sequel_pretty_print

## Usage

```ruby
# Make all model subclasses use pretty_print (called before loading subclasses)
Sequel::Model.plugin :pretty_print

# Make the Artist class use pretty_print
Artist.plugin :pretty_print
```

The pretty_print plugin provides models with a `pretty_print` implementation (see [Ruby PrettyPrint module](http://ruby-doc.org/stdlib/libdoc/prettyprint/rdoc/PrettyPrint.html)) that can be used by tools like Pry. Assuming that we have class `Album` with columns `id` and `name` this provides the following functionality in Pry:

```ruby
# Before:
Artist.new
# => #<Artist @values={}>

# After:
Artist.new
# => #<Artist:0x00007f8d1967f8b0 id: nil, name: nil>
Artist.new(name: "Elvis")
# => #<Artist:0x00007f8d1b413ef8 id: nil, name: "Elvis">
```