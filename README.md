# Test Fixtures

A test fixture is a fixed state of objects used as a baseline for running tests. The purpose of a test fixture is to ensure that there is a fixed environment in which tests are run so that results are repeatable and consistent.

We have seen fixtures in many of our tests already. Here is an example:

```ruby

RSpec.describe House do
  def house_attrs
    {
      bedrooms: 2,
      bathroom: 2,
    }
  end

  it "has watertight roof" do
    house = House.new(house_attrs)
    house.install_new_roof
    expect(house.watertight_roof?).to eq true
  end

  it "has white walls" do
    house = House.new(house_attrs)
    expect(house.wall_color).to eq "white"
  end
end
```

In this example, `house_attrs` holds our fixture. The fixture is a hash of data, and serves to prepare for a consistent initialization of a `House`.

A fixture can be as small as a single character, although there would not be much use for that. It can also be as large as you want it. A common use case for fixtures are to "stub" out responses from third party services, like an HTTP response from a Google query, which could amount to hundreds of lines of code. When fixtures get particularly large, they are sometimes moved to test helper files, to not distract from the purpose of a particular set of tests.

One crucial detail to remember about fixtures is that they are not dynamic, but represent a "fixed" state.
