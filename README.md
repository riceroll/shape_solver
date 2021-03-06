# shape_solver

This is a Python interface for the [ShapeOp](http://shapeop.org/) geometric
constraint solver. It improves on the SWIG interface by providing a more
natural way to express constraints in the Python language.


## Install
```bash
git clone https://github.com/riceroll/shape_solver.git
cd shape_solver
git clone https://github.com/riceroll/ShapeOp.git
bash build.sh
```
change python library location in
``shape_solver/ShapeOp/libShapeOp/bindings/python/CMakeLists.txt``
 


## Finding 2D solutions

ShapeOp finds 3-dimensional solutions. To constrain the solution to be on the
plane z = 0, define 3 non-colinear points on that plane and then constrain all
points to be coplanar with them.

    z1 = s.point((1.0, 0.0, 0.0))
    z2 = s.point((0.0, 1.0, 0.0))
    z3 = s.point((1.0, 1.0, 0.0))
    s.add(PlaneConstraint(s.all_points()))

## Shortcomings

Some constraints such as `AngleConstraint` should allow you to specify
additional parameters (e.g., `minAngle` and `maxAngle`) but this is not
exposed by the SWIG interface.
